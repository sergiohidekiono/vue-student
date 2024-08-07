<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
             <v-img :src="require('assets/logo.png')" class="my-3" contain height="200" />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <HelloWorld/>
      <StudentList/>
    </v-main>

  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import StudentList from './components/student-list';

export default {
  name: 'App',

  components: {
    HelloWorld,
    StudentList,
  },

  data: () => ({
    //
  }),
};
</script>
