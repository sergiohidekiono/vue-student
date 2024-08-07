<template>
    <v-app>
        <!-- Coloque o v-navigation-drawer fora do grid para garantir que ele não interfira -->
        <v-navigation-drawer v-model="drawer" app clipped :permanent="false">
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
        </v-navigation-drawer>

        <v-container>
            <!-- Imagem posicionado corretamente fora do fluxo de grid -->
            <v-row class="ma-0">
                <v-col cols="12" class="pa-0">
                    <div class="d-flex align-start">
                        <v-img :src="require('../assets/logo.png')" class="my-3" />
                    </div>
                </v-col>
            </v-row>

            <!-- Conteúdo principal -->
            <v-row>
                <v-col cols="2">
                    <!-- Menu lateral já posicionado fora do grid -->
                </v-col>
                <v-col cols="10">
                    <v-row class="d-flex justify-center">
                        <span>Consulta de alunos</span>
                    </v-row>
                    <v-row>
                        <v-text-field label="Digite sua busca"></v-text-field>
                        <v-btn depressed> Normal </v-btn>
                        <v-btn :loading="loading3" :disabled="loading3" color="grey" class="ma-2 white--text"
                            @click="loader = 'loading3'"> Cadastrar Aluno </v-btn>
                    </v-row>
                    <v-row>
                        <v-data-table :headers="headers" :items="desserts" :items-per-page="5"
                            class="elevation-1"></v-data-table>
                    </v-row>
                </v-col>
            </v-row>
        </v-container>
    </v-app>
</template>

<script>
export default {
    name: 'StudentList',
    data() {
        return {
            drawer: false,
            headers: [
                { text: 'Registro Acadêmico', value: 'register' },
                { text: 'Nome', value: 'name' },
                { text: 'CPF', value: 'document' },
                { text: 'Ações', value: 'action' }
            ],
            desserts: [
                { register: 101235, name: 'Paula Souza', document: '121.999.999-99', action: 0 },
                { register: 111687, name: 'João Silva', document: '122.999.999-99', action: 0 },
                { register: 111365, name: 'Marina Miranda', document: '123.999.999-99', action: 0 },
                { register: 101299, name: 'Maurício Souza', document: '124.999.999-99', action: 0 },
            ],
            loading3: false,
        };
    }
};
</script>

<style scoped>
.header-table {
    color: white;
    padding: 0 !important;
}

.v-list-item.theme--light {
    padding: 0 !important;
    background: #999999;
}

.v-list-item.v-list-item--link.theme--light {
    background: white;
}

.v-navigation-drawer {
    z-index: 1;
    /* Garanta que o menu lateral tenha um z-index superior para não sobrepor outros elementos */
}
</style>