<template>
    <v-container>
        <v-row cols="12">
            <div class="d-flex align-start">
                <v-img :src="require('../assets/logo.png')" class="my-3" />
            </div>
        </v-row>
        <v-row cols="12">
            <v-col cols="2">
                <v-navigation-drawer floating permanent>
                    <v-list dense>
                        <v-list-item v-for="item in items" :key="item.title" :link="item.link">
                            <v-list-item-content>
                                <v-list-item-title>{{ item.title }}</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-navigation-drawer>
                <!-- <v-navigation-drawer v-model="drawer" app clipped :permanent="false">
                    <v-list>
                        <v-list-item>
                            <v-list-item-content class="header-table" style="padding: 0 !important;">
                                <v-list-item-title style="padding: 0; margin: 0;">
                                    <h4 class="d-flex justify-center">Módulo Acadêmico</h4>
                                </v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                        <v-list-item link>
                            <v-list-item-content style="padding: 0;">
                                <v-list-item-title class="ml-4">Alunos</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-navigation-drawer> -->
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
            items: [
                { title: 'Módulo Acadêmico', link: false },
                { title: 'Alunos', link: true},
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
    color: white;
    padding: 0 !important;
}

.v-list-item.theme--light {
    padding: 0 !important;
    background: #999999;
}

.v-list.v-sheet.theme--light {
    padding: 0 !important;
}

.v-list-item.v-list-item--link.theme--light {
    background: white;
}
</style>