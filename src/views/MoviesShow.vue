<template>
  <div class="movies-show">
    <h2>{{ movie.title }}</h2>
    <p>{{ movie.director }}</p>
    <p>{{ movie.year }}</p>
    <p>{{ movie.plot }}</p>
    <router-link v-bind:to="`/movies/${movie.id}/edit`">Edit Movie</router-link>
    |
    <button v-on:click="destroyMovie(movie)">Delete Movie</button>
    |
    <router-link to="/movies">Back to Movies</router-link>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      movie: {},
    };
  },
  created: function () {
    axios.get("/movies/" + this.$route.params.id).then((response) => {
      console.log("movies show", response);
      this.movie = response.data;
    });
  },
  methods: {
    destroyMovie: function (movie) {
      axios.delete("/movies/" + movie.id).then((response) => {
        console.log("movies destroy", response);
        this.$router.push("/movies");
      });
    },
  },
};
</script>
