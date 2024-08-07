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
            </v-col>
            <v-col cols="10">
                <v-row cols="12" justify="center">
                    <v-row>
                        <span>Consulta de alunos</span>
                    </v-row>
                    <v-row>
                        <v-text-field label="Digite sua busca"></v-text-field>
                        <v-btn depressed> Normal </v-btn>
                        <v-btn :loading="loading3" :disabled="loading3" color="blue-grey" class="ma-2 white--text"
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
            headers: [
                {
                    text: 'Registro Acadêmico',
                    value: 'name',
                },
                { text: 'Nome', value: 'calories' },
                { text: 'CPF', value: 'fat' },
                { text: 'Ações', value: 'carbs' }
            ],
            desserts: [
                {
                    name: 'Frozen Yogurt',
                    calories: 159,
                    fat: 6.0,
                    carbs: 24,
                    protein: 4.0,
                    iron: 1,
                },
                {
                    name: 'Ice cream sandwich',
                    calories: 237,
                    fat: 9.0,
                    carbs: 37,
                    protein: 4.3,
                    iron: 1,
                },
                {
                    name: 'Eclair',
                    calories: 262,
                    fat: 16.0,
                    carbs: 23,
                    protein: 6.0,
                    iron: 7,
                },
                {
                    name: 'Cupcake',
                    calories: 305,
                    fat: 3.7,
                    carbs: 67,
                    protein: 4.3,
                    iron: 8,
                },
                {
                    name: 'Gingerbread',
                    calories: 356,
                    fat: 16.0,
                    carbs: 49,
                    protein: 3.9,
                    iron: 16,
                },
                {
                    name: 'Jelly bean',
                    calories: 375,
                    fat: 0.0,
                    carbs: 94,
                    protein: 0.0,
                    iron: 0,
                },
                {
                    name: 'Lollipop',
                    calories: 392,
                    fat: 0.2,
                    carbs: 98,
                    protein: 0,
                    iron: 2,
                },
                {
                    name: 'Honeycomb',
                    calories: 408,
                    fat: 3.2,
                    carbs: 87,
                    protein: 6.5,
                    iron: 45,
                },
                {
                    name: 'Donut',
                    calories: 452,
                    fat: 25.0,
                    carbs: 51,
                    protein: 4.9,
                    iron: 22,
                },
                {
                    name: 'KitKat',
                    calories: 518,
                    fat: 26.0,
                    carbs: 65,
                    protein: 7,
                    iron: 6,
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