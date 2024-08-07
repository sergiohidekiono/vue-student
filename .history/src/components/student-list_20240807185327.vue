<template>
    <v-container>
        <v-row class="ml-5">
            <div class="d-flex align-start">
                <v-img :src="require('../assets/logo.png')" class="my-3" width="120" />
            </div>
        </v-row>
        <v-row>
            <v-col cols="2" class="menu">
                <v-navigation-drawer floating permanent>
                    <v-list dense>
                        <v-list-item-title class="header text-center">
                            <h4 class="py-2">Módulo Acadêmico</h4>
                        </v-list-item-title>
                        <v-list-item v-for="item in menus" :key="item.title" link>
                            <v-list-item-content>
                                <v-list-item-title>{{ item.title }}</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-navigation-drawer>
            </v-col>
            <v-col cols="10" class="table">
                <template v-if="!showDialog">
                    <v-row justify="center" class="pa-1 header">
                        <span>Consulta de alunos</span>
                    </v-row>
                    <v-row class="wrap-buttons">
                        <v-col cols="7" class="p-0">
                            <v-text-field label="Digite sua busca" v-model="formData.name"></v-text-field>
                        </v-col>
                        <v-col cols="2" class="p-0">
                            <v-btn depressed class="btn-search font-weight-bold" @click="fetchStudentById"> Pesquisar
                            </v-btn>
                        </v-col>
                        <v-col cols="3">
                            <v-btn color="grey" class="ma-2 white--text" @click="createStudent(item);">
                                Cadastrar Aluno
                            </v-btn>
                        </v-col>
                    </v-row>
                    <v-data-table :headers="headers" :items="students" :items-per-page="5" class="elevation-1">
                        <template v-slot:[`item.action`]="{ item }">
                            <v-btn @click="editStudent(item);" icon>
                                <v-icon>mdi-pencil</v-icon>
                            </v-btn>
                            <v-btn @click="deleteStudent(item)" icon>
                                <v-icon>mdi-delete</v-icon>
                            </v-btn>
                        </template>
                    </v-data-table>
                </template>
                <template v-if="showDialog">
                    <v-row justify="center" class="pa-1 header">
                        <span v-if="isRegister">Cadastro de aluno</span>
                        <span v-if="!isRegister">Editar aluno</span>
                    </v-row>
                    <register-edit-student @dialog="receiveValueWatch" :student-id="selectedStudentId" />
                </template>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import axios from 'axios';
import RegisterEditStudent from './register-edit-student.vue';

export default {
    name: 'StudentList',
    components: {
        RegisterEditStudent
    },
    data() {
        return {
            showDialog: false,
            isRegister: false,
            selectedStudentId: null,
            formData: {
                name: '',
            },
            menus: [
                { title: 'Alunos' },
            ],
            students: [],
            headers: [
                { text: 'Registro Acadêmico', value: 'register' },
                { text: 'Nome', value: 'name' },
                { text: 'CPF', value: 'document' },
                { text: 'Ações', value: 'action' }
            ],
        }
    },
    created() {
        this.fetchStudents();
    },
    computed: {
        fetchStudentById() {
            this.fetchStudents();
            return this.students = this.students.filter((student) => student.name.toLowerCase().includes(this.formData.name.toLowerCase()));
            // console.log(this.students)
            
        },
    },
    methods: {
        receiveValueWatch(value) {
            if (value) {
                this.fetchStudents();
            }
            this.showDialog = false;
        },
        createStudent() {
            this.selectedStudentId = null;
            this.showDialog = true;
            this.isRegister = true;
        },
        editStudent(item) {
            this.selectedStudentId = item.id;
            this.showDialog = true;
            this.isRegister = false;
        },
        fetchStudentById() {
            this.fetchStudents();
            this.students = this.students.filter((student) => student.name.toLowerCase().includes(this.formData.name.toLowerCase()));
            console.log(this.students)
            this.students
        },
        async deleteStudent(student) {
            try {
                await axios.delete(`http://localhost:3000/students/${student.id}`);
                this.fetchStudents();
            } catch (error) {
                console.error('Erro ao tentar excluir o estudante:', error.response ? error.response.data : error.message);
            }
        },
        async fetchStudents() {
            try {
                const response = await axios.get("http://localhost:3000/students");
                this.students = response.data;
            } catch (error) {
                console.log('Erro ao buscar estudante!', error);
            }
        }
    }
}
</script>


<style scoped>
.menu {
    padding: 0 !important;
    border: 2px solid;
    border-radius: 5px 0 0 5px;

    .v-list.v-sheet.theme--light {
        padding: 0 !important;
    }

    .header {
        padding: 0 !important;
        background: #999999;
        color: white;
    }
}

.table {
    border-left: 0;
    border-right: 2px;
    border-top: 2px;
    border-bottom: 2px;
    border-style: solid;
    border-radius: 0 5px 5px 0;

    .header {
        background: #f0f0f0;
        border-bottom: 2px solid;
    }
}

.btn-search {
    background-color: #CCCCCC !important;
    color: black;
}

.wrap-buttons {
    display: flex;
    align-items: baseline;
}
</style>