<template>
  <v-app>
    <MovieTable />
  </v-app>
</template>

<script>
import MovieTable from "./components/MovieTable.vue";

export default {
  components: {
    MovieTable,
  },
};
</script>

<style>
@import 'vuetify/styles';
</style>
