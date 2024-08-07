<template>
    <v-row justify="center">

        <v-dialog v-model="localDialog" max-width="290">
            <v-card>
                <v-card-title class="text-h5">
                    Use Google's location service?
                </v-card-title>

                <v-card-text>
                    Let Google help apps determine location. This means sending anonymous location data to Google, even
                    when no apps are running.
                </v-card-text>

                <v-card-actions>
                    <v-spacer></v-spacer>

                    <v-btn color="green darken-1" text @click="localDialog = false">
                        Disagree
                    </v-btn>

                    <v-btn color="green darken-1" text @click="localDialog = false">
                        Agree
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