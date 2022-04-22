<template>
  <div class="bg-dark p-5 text-light">
    <div class="container-lg text-light">
      <!-- MOVIES CONTAINER -->
      <div class="row black">
        <h2 class="text-danger">Movies</h2>
        <div class="col-12 d-flex flex-wrap justify-content-center">
          <div
            class="card bg-transparent w_20"
            v-for="(movie, i) in movies"
            :key="i"
          >
            <img
              class="cover"
              :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path"
              alt="cover-movie"
            />
            <div class="card-body bg_color">
              <h3 class="card-title text-secondary">
                {{ movie.title ? movie.title : movie.name }}
              </h3>
              <h4>{{ movie.original_title }}</h4>
              <p class="card-text">
                {{ movie.original_language }}

                <lang-flag :iso="movie.original_language" />
              </p>
              <p>{{ movie.vote_average }}</p>
            </div>
          </div>
        </div>
      </div>
      <!--/ MOVIES CONTAINER -->

      <!-- SERIES CONTAINER -->
      <div class="row black">
        <h2 class="text-danger">TV Series</h2>
        <div class="col-12 d-flex flex-wrap justify-content-center">
          <div
            class="card bg-transparent w_20"
            v-for="(serie, i) in series"
            :key="i"
          >
            <img
              class="cover"
              :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path"
              alt="cover-serie"
            />
            <div class="card-body bg_color">
              <h3 class="card-title text-secondary">
                {{ serie.name }}
              </h3>
              <h4>{{ serie.original_title }}</h4>
              <p class="card-text">
                {{ serie.original_language }}

                <lang-flag :iso="serie.original_language" />
              </p>
              <p>{{ serie.vote_average }}</p>
            </div>
          </div>
        </div>
      </div>
      <!--/ SERIES CONTAINER -->
    </div>
  </div>
</template>

<script>
export default {
  name: "MyMain",

  data() {
    return {
      flags: ["it", "en", "de"],
    };
  },
  methods: {},
  props: {
    movies: Array,
    series: Array,
  },
};
</script>

<style>
.w_20 {
  width: 20rem;
}
.bg_color {
  background-color: #2d2d2d;
}
.flag {
  height: 20px;
  width: 20px;
}
</style>
