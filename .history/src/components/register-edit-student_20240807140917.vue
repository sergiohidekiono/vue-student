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
                        <v-text-field label="RA" required v-model="formData.ra"></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field label="CPF" required v-model="formData.cpf"></v-text-field>
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
                nome: '',
                email: '',
                ra: '',
                cpf: ''
            }
        };
    },
    created() {
        if (this.studentId) {
            this.fetchStudentData(this.studentId);
        }
    },
    methods: {
        async fetchStudentData(id) {
            const response = await axios.get(`http://localhost:3000/students?id=${id}`);
            console.log('ALUNO: ', response.data[0]);
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

                await axios.post('http://localhost:3000/students', {
                    id: newId.toString(),
                    name: this.formData.name,
                    email: this.formData.email,
                    register: this.formData.ra,
                    document: this.formData.cpf
                });

                this.$emit('dialog', true);
            } catch (error) {
                console.error('Erro ao salvar os dados:', error);

            }
        }
    }
}
</script>

<style lang="scss" scoped></style>