<template>
  <div class="bg-dark p-5 text-light">
    <div class="container-lg text-light">
      <!-- MOVIES CONTAINER -->
      <div class="row black">
        <h2 class="text-danger p-4 m-0p-3">Movies</h2>
        <div class="col-12 d-flex flex-wrap justify-content-center">
          <div
            class="card bg-transparent w_20"
            v-for="(movie, i) in movies"
            :key="i"
          >
            <img
              class="cover card-img"
              v-if="movie.poster_path != null"
              :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path"
              alt="cover-movie"
            />
            <img
              class="cover"
              v-else
              src="https://www.altavod.com/assets/images/poster-placeholder.png"
              alt="cover-movie"
            />
            <div class="card-body bg_color d_flex">
              <h3 class="card-title text-secondary">
                Title:
                {{ movie.title ? movie.title : movie.name }}
              </h3>
              <h4>Original title: {{ movie.original_title }}</h4>
              <p class="card-text">
                {{ movie.original_language }}

                <lang-flag :iso="movie.original_language" />
              </p>
              <p>Voto: {{ Math.round(movie.vote_average / 2) }}.</p>
              <div class="star_rating">
                <star-rating
                  :inline="true"
                  :star-size="20"
                  :read-only="true"
                  :show-rating="false"
                  v-bind:max-rating="Math.round(movie.vote_average / 2)"
                  inactive-color="#ffff00"
                >
                </star-rating>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!--/ MOVIES CONTAINER -->

      <!-- SERIES CONTAINER -->
      <div class="row black">
        <h2 class="text-danger p-4 m-0">TV Series</h2>
        <div class="col-12 d-flex flex-wrap justify-content-center">
          <div
            class="card bg-transparent w_20"
            v-for="(serie, i) in series"
            :key="i"
          >
            <img
              class="cover"
              v-if="serie.poster_path != null"
              :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path"
              alt="cover-movie"
            />
            <img
              class="cover"
              v-else
              src="https://www.altavod.com/assets/images/poster-placeholder.png"
              alt="cover-movie"
            />
            <div class="card-body bg_color d_flex">
              <h3 class="card-title text-secondary">Title: {{ serie.name }}</h3>
              <h4>Original title: {{ serie.original_name }}</h4>
              <p class="card-text">
                {{ serie.original_language }}

                <lang-flag :iso="serie.original_language" />
              </p>
              <p>Vote: {{ Math.round(serie.vote_average / 2) }}.</p>
              <div class="star_rating">
                <star-rating
                  :inline="true"
                  :star-size="20"
                  :read-only="true"
                  :show-rating="false"
                  v-bind:max-rating="Math.round(serie.vote_average / 2)"
                  inactive-color="#ffff00"
                >
                </star-rating>
              </div>
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
.d_flex {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: center;
}
.flag {
  height: 20px;
  width: 20px;
}
</style>
