<template>
    <v-container>
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
    </v-container>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped></style>