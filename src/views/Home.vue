<template>
  <div class="home">
    <h2>Add Movie!</h2>
    <button v-on:click="createMovie()">Add new Movie</button>
    <h1>{{ message }}</h1>
    <div v-for="movie in movies" :key="movie.id">
      <h2>Title: {{ movie.title }}</h2>
      <h3>Plot: {{ movie.plot }}</h3>
    </div>
  </div>
</template>
<style></style>
<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Here are your Movies",
      movies: [],
    };
  },
  created: function () {
    this.indexMovies();
  },
  methods: {
    indexMovies: function () {
      axios.get("http://localhost:3000/movies").then((response) => {
        this.movies = response.data;
        console.log("All Movies:", this.movies);
      });
    },
    createMovie: function () {
      console.log("Add Movie");
      var params = {
        title: "Once Upon a Time in Hollywood",
        year: 2019,
        plot: "Actor Rick Dalton gained fame and fortune by starring in a 1950s television Western, but is now struggling to find meaningful work in a Hollywood that he doesn't recognize anymore.",
        director: "Quentin Tarantino",
      };
      axios
        .post("http://localhost:3000/movies", params)
        .then((response) => {
          console.log("Success!", response.data);
          this.movies.push(response.data);
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>