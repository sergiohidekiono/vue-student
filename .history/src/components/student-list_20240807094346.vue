<template>
    <v-container>
        <v-row>
            <div class="d-flex align-start">
                <v-img :src="require('../assets/logo.png')" class="my-3" />
            </div>
        </v-row>
        <v-row>
            <v-col cols="2">
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

export default {

};

</script>

<style scoped>
.v-list-item.theme--light .header-table {
    color: white;
    background: #999999;
    padding: 0 !important;
}

.v-list-item.theme--light {
    padding: 0 !important;
}

.v-list.v-sheet.theme--light {
    padding: 0 !important;
}

.v-list-item__content{
    padding: 10px;
}
</style>