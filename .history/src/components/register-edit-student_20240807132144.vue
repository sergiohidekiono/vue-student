<template>
    <v-container>
        <v-card-text>
            <v-container>
                <v-row>
                    <v-col cols="12">
                        <v-text-field label="Nome" required></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field label="E-mail" required></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field label="RA" required></v-text-field>
                    </v-col>
                    <v-col cols="12">
                        <v-text-field label="CPF" required></v-text-field>
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
export default {
    data() {
        return {
            localDialog: false,
        };
    },
    methods: {
        closeDialog() {
            this.$emit('dialog', false);
        },
        saveDialog() {
            this.$emit('dialog', false);
        }
    }
}
</script>

<style lang="scss" scoped></style>