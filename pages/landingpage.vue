<template>
  <div class="landing-div">
    <h1 class="landing-title">Welcome to the movies app,Hello</h1>
    <div class="popular-list"></div>
    <Movies :movies="movies" />
  </div>
</template>
<script>
import axios from "axios";
import Movies from "../components/Movies.vue";
export default {
  name: "landingpage",
  data() {
    return {
      movies: []
    };
  },
  async created() {
    const config = {
      header: {
        Accept: "application/json"
      }
    };
    const res = await axios.get(
      "https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&&api_key=e2f4de34eb267eaeb8fe1c90c2a532c6",
      config
    );
    // console.log("RES", res.data.results);
    const movieres = res.data.results;
    // console.log("Movies=>", movieres);
    const movstring = JSON.stringify(movieres);
    const mov = JSON.parse(movstring);
    // console.log("MOV", mov);
    mov.map(movie => {
      this.movies.push(movie);
    });

    console.log(this.movies);
    this.showMovies();
  },
  methods: {
    showMovies() {}
  }
};
</script>

<style scoped>
.landing-div {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.landing-title {
  font-weight: bold;
  font-family: "Courier New", Courier, monospace;
}
</style>
