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
      <div :class="toggleDesc ? 'desc-container' : 'desc-box'">
        {{ result.overview }}
      </div>
      <b-card-text class="card-text-element">
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

      <b-button variant="primary" class="card-btn" @click="Toggle()"
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
  data() {
    return {
      toggleDesc: true
    };
  },
  mounted() {},
  methods: {
    Toggle() {
      this.toggleDesc = !this.toggleDesc;
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
</style>
