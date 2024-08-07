<template>
  <v-app>
    <v-main>
      <StudentList />
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

  data: () => ({
    //
  }),
};
</script>
