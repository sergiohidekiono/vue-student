<template>
  <v-app>
    <v-main class="wrapper">
      <StudentList class="wrapper" />
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

</style>