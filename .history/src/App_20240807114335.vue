<template>
  <v-app>
    <v-main class="wrapper">
      <StudentList class="wrapper d-flex justify-center" />
    </v-main>
  </v-app>
</template>

<script>
import StudentList from './components/student-list';

export default {
  name: 'App',

  components: {
    StudentList,
  },

  data: () => ({}),
};
</script>

<style>
.wrapper {
  width: 100vw;
  height: 100vh;
  margin: 0;
}
</style>