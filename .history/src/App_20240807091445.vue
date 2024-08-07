<template>
  <v-app>
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
