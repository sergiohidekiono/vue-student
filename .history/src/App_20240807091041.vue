<template>
  <v-app>
    <div class="d-flex align-start">
      <v-img :src="require('./assets/logo.png')" class="my-3" contain height="60" />
    </div>

    <v-main>
      <HelloWorld />
      <StudentList />
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
