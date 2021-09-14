<template>
  <div class="movie-div">
    <!-- https://picsum.photos/600/300/?image=25 -->
    <div>
      <b-card
        :title="movie.title"
        :img-src="img"
        img-alt="Image"
        img-top
        style="max-width: 20rem;"
        class="mb-2 movie-card"
      >
        <div :class="toggleDesc ? 'desc-box' : 'desc-container'">
          {{ movie.overview }}
        </div>

        <b-card-text>
          <h5 class="rating-container">
            Rating:
            <h5>
              <h5 class="rating-primary">{{ movie.vote_average }}</h5>
              with
              <h5 class="rating-primary">{{ movie.vote_count }}</h5>
              Votes
            </h5>
          </h5>
        </b-card-text>

        <b-button
          href="#"
          variant="primary"
          class="card-btn"
          @click="ToggleDesc(movie)"
          >Movie Description</b-button
        >
      </b-card>
    </div>
  </div>
</template>
<script>
// import "node_modules/bootstrap/scss/bootstrap.scss";
// import "node_modules/bootstrap-vue/src/index.scss";
import axios from "axios";
export default {
  name: "movie",
  props: {
    movie: Object,
    img: String
  },
  data() {
    return {
      toggleDesc: Boolean
    };
  },
  mounted() {
    this.toggleDesc = false;
  },
  methods: {
    ToggleDesc(movie) {
      //   const descbox = document.querySelector(".desc-container");

      //   if (this.toggleDesc === false) {
      //     descbox.style.overflow = "scroll";
      //     this.toggleDesc = true;
      //   } else if (this.toggleDesc === true) {
      //     descbox.style.overflow = "hidden";
      //     descbox.style.textOverflow = "ellipsis";
      //     this.toggleDesc = false;
      //   }
      //   console.log("this", this.toggleDesc);
      //   console.log(movie.vote_average);
      this.toggleDesc = !this.toggleDesc;
    }
  }
};
</script>
<style scoped>
.movie-div {
  flex-basis: 33%;
  padding: 1rem;
}
.movie-card {
  height: 30rem;
  padding: 1rem;
}
.card-body {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.card-btn {
  background: lightcoral;
}
.rating-primary {
  display: inline;
  color: lightseagreen;
}
.desc-container {
  display: inline-block;
  width: 100%;
  height: 5.15rem;
  -webkit-line-clamp: 5;
  display: -webkit-box;
  line-height: 1;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
.card-title {
  display: inline-block;
  width: 100%;
  height: 1.6rem;
  -webkit-line-clamp: 1;
  display: -webkit-box;
  line-height: 1;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}
.desc-box {
  display: inline-block;
  width: 100%;
  height: 5.15rem;
  -webkit-line-clamp: 5;
  display: -webkit-box;
  line-height: 1;
  -webkit-box-orient: vertical;
  overflow: scroll;
  text-overflow: scroll;
}
</style>
