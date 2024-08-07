<template>
    <v-row justify="center">
        <v-dialog v-model="localDialog" persistent max-width="600px">
            <v-card>
                <v-card-title>
                    <span class="text-h5">Cadastrar Aluno</span>
                </v-card-title>
                <v-card-text>
                    <v-container>
                        <v-row>
                            <v-col cols="12">
                                <v-text-field label="Nome" required></v-text-field>
                            </v-col>
                            <v-col cols="12">
                                <v-text-field label="E-mail" type="password" required></v-text-field>
                            </v-col>
                            <v-col cols="12">
                                <v-text-field label="RA" required></v-text-field>
                            </v-col>
                            <v-col cols="12">
                                <v-text-field label="CPF" type="password" required></v-text-field>
                            </v-col>
                        </v-row>
                    </v-container>
                    <small>*indicates required field</small>
                </v-card-text>
                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="blue darken-1" text @click="localDialog = false">
                        Close
                    </v-btn>
                    <v-btn color="blue darken-1" text @click="localDialog = false">
                        Save
                    </v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-row>
</template>

<script>
export default {
    props: {
        dialog: {
            type: Boolean,
            required: true
        }
    },
    data() {
        return {
            localDialog: this.dialog
        }
    },
    watch: {
        dialog(newVal) {
            this.localDialog = newVal;
        },
        localDialog(newVal) {
            this.$emit('update:dialog', newVal);
        }
    },
    methods: {
        closeDialog() {
            console.log('fui clicado pra fechar')
            this.$emit('close', false);
        },
        saveStudent() {
            // Lógica para salvar o estudante
            this.closeDialog();
        }
    }
}
</script>

<style lang="scss" scoped></style>