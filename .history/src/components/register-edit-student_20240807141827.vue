<template>
    <v-container>
        <v-card-text>
            <v-container>
                <v-row>
                    <v-col cols="12">
                        <v-text-field label="Nome" required v-model="formData.name"></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field label="E-mail" required v-model="formData.email"></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field label="RA" required v-model="formData.register"></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field label="CPF" required v-model="formData.document"></v-text-field>
                    </v-col>
                </v-row>
            </v-container>
        </v-card-text>
        <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="grey" class="ma-2 white--text" @click="closeDialog"> Cancelar </v-btn>
            <v-btn color="grey" class="ma-2 white--text" @click="saveDialog"> Salvar </v-btn>
        </v-card-actions>
    </v-container>
</template>

<script>
import axios from 'axios';

export default {
    props: {
        studentId: {
            type: String
        }
    },
    data() {
        return {
            localDialog: false,
            formData: {
                name: '',
                email: '',
                register: '',
                document: ''
            }
        };
    },
    created() {
        if (this.studentId) {
            this.fetchStudentData(this.studentId);
        } else {
            this.formData = {
                name: '',
                email: '',
                register: '',
                document: ''
            }
        }
    },
    methods: {
        async fetchStudentData(id) {
            const response = await axios.get(`http://localhost:3000/students?id=${id}`);
            this.formData.name = response.data[0].name;
            this.formData.email = response.data[0].email;
            this.formData.register = response.data[0].register;
            this.formData.document = response.data[0].document;
        },
        closeDialog() {
            this.$emit('dialog', false);
        },
        async saveDialog() {
            try {
                const response = await axios.get('http://localhost:3000/students');
                const students = response.data;

                const maxId = students.reduce((max, student) => Math.max(max, parseInt(student.id, 10)), 0);
                const newId = maxId + 1;

                if (this.studentId) {
                    await axios.put(`http://localhost:3000/students/${this.studentId}`, {
                        id: newId.toString(),
                        name: this.formData.name,
                        email: this.formData.email,
                        register: this.formData.register,
                        document: this.formData.document
                    });

                } else {
                    await axios.post('http://localhost:3000/students', {
                        id: newId.toString(),
                        name: this.formData.name,
                        email: this.formData.email,
                        register: this.formData.register,
                        document: this.formData.document
                    });
                }
                this.$emit('dialog', true);
            } catch (error) {
                console.error('Erro ao salvar os dados:', error);

            }
        }
    }
}
</script>

<style lang="scss" scoped></style>