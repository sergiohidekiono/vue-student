<template>
    <v-container>
        <v-row>
            <div class="d-flex align-start">
                <v-img :src="require('../assets/logo.png')" class="my-3" />
            </div>
        </v-row>
        <!-- <v-row>
            <v-col cols="2">
                <v-row class="">
                    <h4>Módulo Acadêmico</h4>
                </v-row>
                <v-row>
                    <span>Alunos</span>
                </v-row>

            </v-col>
            <v-col cols="10">
                <v-row cols="12" class="d-flex justify-center">
                    <span>Consulta de alunos</span>
                </v-row>
            </v-col>
        </v-row> -->
        <v-row>
            <v-col cols="2">
                <v-navigation-drawer v-model="drawer" app clipped :permanent="false">
                    <v-list>
                        <v-list-item>
                            <v-list-item-content class="header-table">
                                <v-list-item-title style="padding: 0; margin: 0;">
                                    <h4>Módulo Acadêmico</h4>
                                </v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                        <v-list-item link>
                            <v-list-item-content>
                                <v-list-item-title>Alunos</v-list-item-title>
                            </v-list-item-content>
                        </v-list-item>
                    </v-list>
                </v-navigation-drawer>
            </v-col>
            <v-col cols="10">
                <v-row cols="12" class="d-flex justify-center">
                    <span>Consulta de alunos</span>
                </v-row>
            </v-col>
        </v-row>

    </v-container>
</template>
<script>
</script>

<style>
.header-table {
    color: white;
    background: #999999;
}
</style>