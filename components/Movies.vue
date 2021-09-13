<template>
  <div class="movies-container">
    <h3 class="search-label">Type here to search movies</h3>
    <input
      type="text"
      placeholder="Enter Movie Name"
      class="search-text"
      @keyup="SearchMovie()"
    />
    <div class="show-search-res-div">
      <div :key="result.id" v-for="result in searchresult">
        {{ result.id }}
        <Searchres
          :result="result"
          :resimg="'https://image.tmdb.org/t/p/original' + result.backdrop_path"
        />
      </div>
    </div>

    <h1 class="popular-title">Most Popular Movies</h1>
    <div class="popular-movie-div">
      <div :key="movie" v-for="movie in movies">
        <Movie
          :movie="movie"
          :img="'https://image.tmdb.org/t/p/original' + movie.backdrop_path"
        />
      </div>
    </div>
  </div>
</template>
<script>
import Movie from "./Movie.vue";
import axios from "axios";
import Searchres from "../components/Searchres.vue";
export default {
  name: "movies",
  props: {
    movies: {
      type: Array
    }
  },
  data() {
    return {
      searchresult: []
    };
  },
  created() {
    console.log("HELLO movies=>", this.movies);
  },
  mounted() {
    const rescontainer = document.querySelector(".show-search-res-div");
    rescontainer.style.display = "none";
  },
  methods: {
    async SearchMovie() {
      const config = {
        header: {
          Accept: "application/json"
        }
      };
      const val = document.querySelector(".search-text").value;
      const rescontainer = document.querySelector(".show-search-res-div");
      console.log("VALUE", val);
      if (val) {
        rescontainer.style.display = "flex";
        const res = await axios.get(
          "https://api.themoviedb.org/3/search/movie?api_key=e2f4de34eb267eaeb8fe1c90c2a532c6&&query=" +
            val,
          config
        );
        this.searchresult = res.data.results;
        console.log("Result", this.searchresult);
      } else {
        console.log("Input Empty");
        this.searchresult = [];
        rescontainer.style.display = "none";
      }
    }
  }
};
</script>
<style scoped>
.popular-title {
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  color: salmon;
}
.popular-movie-div {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
.movies-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.search-label {
  color: mediumslateblue;
}
.search-text {
  padding: 0.5rem;
  border: 2px solid red;
}
div.show-search-res-div {
  display: flex;
  flex-wrap: wrap;
  margin: 2rem 5rem;
  justify-content: space-around;
  width: 80%;
  flex-direction: row;
  border: 5px solid royalblue;
  padding: 1rem;
}
</style>
