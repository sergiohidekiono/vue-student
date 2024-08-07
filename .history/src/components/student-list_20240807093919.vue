<template>
    <v-app>
        <v-container>
            <v-row>
                <div class="d-flex align-start">
                    <v-img :src="require('../assets/logo.png')" class="my-3" />
                </div>
            </v-row>
            <v-row>
                <!-- Definição do menu lateral fora do grid -->
                <v-navigation-drawer v-model="drawer" app clipped :permanent="false">
                    <v-list>
                        <v-list-item>
                            <v-list-item-content class="header-table" style="padding: 0 !important;">
                                <v-list-item-title style="padding: 0; margin: 0;">
                                    <h4>Módulo Acadêmico</h4>
                                </v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                        <v-list-item link>
                            <v-list-item-content style="padding: 0;">
                                <v-list-item-title>Alunos</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-navigation-drawer>
                <!-- Conteúdo principal dentro do grid -->
                <v-col cols="10">
                    <v-row class="d-flex justify-center">
                        <span>Consulta de alunos</span>
                    </v-row>
                </v-col>
            </v-row>
        </v-container>
    </v-app>
</template>

<script>
export default {
    data() {
        return {
            drawer: false
        };
    }
};
</script>

<style scoped>
.header-table {
    color: white;
    background: #999999;
    padding: 0 !important;
}
</style>