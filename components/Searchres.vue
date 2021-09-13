<template>
  <div class="res-container">
    <b-card
      :title="result.title"
      :img-src="
        resimg === 'https://image.tmdb.org/t/p/originalnull'
          ? '/no-image-available.jpeg'
          : resimg
      "
      img-alt="Image"
      img-top
      tag="article"
      style="max-width: 20rem;"
      class="mb-2 movie-card"
    >
      <b-card-text class="card-text-element">
        <p class="hell">hello</p>

        <h5 class="rating-container">
          Rating:
          <h5>
            <h5 class="rating-primary">{{ result.vote_average }}</h5>
            with
            <h5 class="rating-primary">{{ result.vote_count }}</h5>
            Votes
          </h5>
        </h5>
      </b-card-text>

      <b-button variant="primary" class="card-btn" @click="Toggle(result.id)"
        >Movie Description</b-button
      >
    </b-card>
  </div>
</template>
<script>
export default {
  name: "searchres",
  props: {
    result: Object,
    resimg: String
  },
  mounted() {
    console.log("MOUNTED===>>", document.querySelector(".res-container"));
  },
  methods: {
    Toggle(id) {
      const x = document.querySelector(".hell");
      console.log("X->", x);
      x.style.color = "purple";
    }
  }
};
</script>
<style scoped>
.res-container {
  flex-basis: 20%;
}
.movie-card {
  height: auto;
}
.card-body {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}
.card-btn {
  background: lightcoral;
}
.rating-primary {
  display: inline;
  color: lightseagreen;
}
</style>
