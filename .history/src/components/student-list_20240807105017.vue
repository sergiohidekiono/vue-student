<template>
    <v-container>
        <v-row>
            <div class="d-flex align-start">
                <v-img :src="require('../assets/logo.png')" class="my-3" />
            </div>
        </v-row>
        <v-row>
            <v-col cols="2" class="wrap-menu">
                <v-navigation-drawer floating permanent>
                    <v-list dense>
                        <v-list-item-title class="menu-header">
                            <h4 class="ps-2">Módulo Acadêmico</h4>
                        </v-list-item-title>
                        <v-list-item v-for="item in menus" :key="item.title" link>
                            <v-list-item-content>
                                <v-list-item-title>{{ item.title }}</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-navigation-drawer>
            </v-col>
            <v-col cols="10">
                <v-row cols="12" justify="center">
                    <v-row>
                        <span>Consulta de alunos</span>
                    </v-row>
                    <v-row>
                        <v-text-field label="Digite sua busca"></v-text-field>
                        <v-btn depressed> Normal </v-btn>
                        <v-btn :loading="loading3" :disabled="loading3" color="grey" class="ma-2 white--text"
                            @click="loader = 'loading3'"> Cadastrar Aluno </v-btn>
                    </v-row>
                    <v-row>
                        <template>
                            <v-data-table :headers="headers" :items="desserts" :items-per-page="5"
                                class="elevation-1"></v-data-table>
                        </template>
                    </v-row>
                </v-row>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    name: 'StudentList',
    data() {
        return {
            menus: [
                { title: 'Alunos' },
            ],
            headers: [
                { text: 'Registro Acadêmico', value: 'register', },
                { text: 'Nome', value: 'name' },
                { text: 'CPF', value: 'document' },
                { text: 'Ações', value: 'action' }
            ],
            desserts: [
                {
                    register: 101235,
                    name: 'Paula Souza',
                    document: '121.999.999-99',
                    action: 0,
                },
                {
                    register: 111687,
                    name: 'João Silva',
                    document: '122.999.999-99',
                    action: 0,
                },
                {
                    register: 111365,
                    name: 'Marina Miranda',
                    document: '123.999.999-99',
                    action: 0,
                },
                {
                    register: 101299,
                    name: 'Maurício Souza',
                    document: '124.999.999-99',
                    action: 0,
                },

            ],
        }
    }
}
</script>

<style scoped>
.v-list-item.theme--light .header-table {
    padding: 0 !important;
}

.wrap-menu {
    padding: 0 !important;
}

.menu-header {
    padding: 0 !important;
    background: #999999;
    color: white;
}

.v-list.v-sheet.theme--light {
    padding: 0 !important;
}

.v-list-item.v-list-item--link.theme--light {
    background: white;
}
</style>