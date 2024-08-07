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
// import axios from 'axios';

export default {
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
    methods: {
        closeDialog() {
            this.$emit('dialog', false);
        },
        saveDialog() {
            console.log('NAME:', this.formData.name);
        }
        // async saveDialog() {
        //     await axios.post('http://localhost:3000/students', {
        //         name: this.name,
        //         email: this.email,
        //         ra: this.ra,
        //         cpf: this.cpf
        //     });
        //     this.$emit('dialog', false);
        // }
    }
}
</script>

<style lang="scss" scoped></style>