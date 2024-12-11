<template>
  <v-container>
    <v-text-field label="Buscar por título" v-model="filters.title" @input="fetchMovies"></v-text-field>
    <v-data-table :headers="headers" :items="movies" class="elevation-1">
      <template v-slot:item.image="{ item }">
        <img :src="item.image" alt="Poster" width="50" />
      </template>
    </v-data-table>
  </v-container>
</template>

<script>
import api from "../services/api";

export default {
  data() {
    return {
      movies: [],
      filters: { title: "" },
      headers: [
        { text: "ID", value: "imdbId" },
        { text: "Título", value: "title" },
        { text: "Año", value: "year" },
        { text: "Imagen", value: "image" },
        { text: "Valoración", value: "personalRating" },
      ],
    };
  },
  methods: {
    async fetchMovies() {
      const response = await api.get("/movies", { params: this.filters });
      this.movies = response.data;
    },
  },
  mounted() {
    this.fetchMovies();
  },
};
</script>
