<template>
  <div class="bg-dark text-light">
    <div class="container">
      <div
        class="row"
        v-if="this.trendingMovies.length != 0 && this.movies.length === 0"
      >
        <h3 class="p-4">Choose for you</h3>
        <HomeTrailer />
      </div>
    </div>
    <div class="container text-light">
      <h3
        v-if="this.trendingMovies.length != 0 && this.movies.length === 0"
      ></h3>
      <div v-if="this.movies.length === 0">
        <HomeCards
          :trendingMovies="trendingMovies"
          :trendingTV="trendingTV"
          type="movie"
        />
      </div>
      <div v-else>
        <!-- HOME CARDS -->

        <!-- / HOME CARDS -->
        <!-- MOVIES CONTAINER -->
        <div class="row black" v-if="this.movies.length > 0">
          <h2 class="text-danger p-4 m-0p-3">Movies</h2>
          <div class="col-12 d-flex flex-wrap justify-content-between">
            <div
              class="card-movie bg-transparent w_20"
              v-for="(movie, i) in movies"
              :key="i"
            >
              <img
                class="cover card-image"
                v-if="movie.poster_path != null"
                :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path"
                alt="cover-movie"
              />
              <img
                class="cover card-image"
                v-else
                src="https://www.altavod.com/assets/images/poster-placeholder.png"
                alt="cover-movie"
              />
              <div class="card-info bg_color d_flex">
                <h3 class="card-title text-white fs-5">
                  Title:
                  {{ movie.title ? movie.title : movie.name }}
                </h3>
                <h4 class="text-danger">
                  Original title: {{ movie.original_title }}
                </h4>
                <p class="card-text">
                  {{ movie.original_language }}

                  <lang-flag :iso="movie.original_language" />
                </p>

                <div class="star_rating d-flex align-items-center m-0">
                  <p>
                    Vote:
                    <star-rating
                      :inline="true"
                      :star-size="20"
                      :read-only="true"
                      :show-rating="false"
                      v-bind:max-rating="Math.round(movie.vote_average / 2)"
                      inactive-color="#ffff00"
                    >
                    </star-rating>
                  </p>
                </div>
                <div>
                  <span>Overview : {{ movie.overview }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!--/ MOVIES CONTAINER -->

        <!-- SERIES CONTAINER -->
        <div class="row black" v-if="series.length > 0">
          <h2 class="text-danger p-4 m-0p-3">TV Series</h2>
          <div class="col-12 d-flex flex-wrap justify-content-between">
            <div
              class="card-serie bg-transparent w_20"
              v-for="(serie, i) in series"
              :key="i"
            >
              <img
                class="cover card-image"
                v-if="serie.poster_path != null"
                :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path"
                alt="cover-serie"
              />
              <img
                class="cover"
                v-else
                src="https://www.altavod.com/assets/images/poster-placeholder.png"
                alt="cover-serie"
              />
              <div class="card-info d_flex">
                <h3 class="card-title text-light fs-5">
                  Title:
                  {{ serie.name }}
                </h3>
                <h4 class="text-danger">
                  Original title: {{ serie.original_name }}
                </h4>
                <p class="card-text">
                  {{ serie.original_language }}

                  <lang-flag :iso="serie.original_language" />
                </p>
                <p>
                  Voto:
                  <star-rating
                    :inline="true"
                    :star-size="20"
                    :read-only="true"
                    :show-rating="false"
                    v-bind:max-rating="Math.round(serie.vote_average / 2)"
                    inactive-color="#ffff00"
                  >
                  </star-rating>
                </p>

                <div>
                  <span>Overview : {{ serie.overview }}</span>
                </div>
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
import HomeCards from "./HomeCards.vue";
import HomeTrailer from "./HomeTrailer.vue";
// import axios from "axios";
export default {
  name: "MyMain",
  components: {
    HomeCards,
    HomeTrailer,
  },

  props: {
    movies: Array,
    series: Array,
    trendingMovies: Array,
    trendingTV: Array,
    id: Array,
  },
};
</script>

<style lang="scss" scoped>
.w_20 {
  width: 20rem;
}
// .bg_color {
//   background-color: #141414;
// }
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
.card-movie,
.card-serie {
  width: 300px;
  height: 450px;
  margin-top: 20px;
  margin-bottom: 40px;
  position: relative;

  img {
    width: 300px;
    height: 450px;
  }
  .card-info {
    width: 300px;
    height: 450px;
    position: absolute;
    top: 0;
    padding: 30px 15px;
    display: none;
    overflow: auto;
  }
}

.card-movie:hover img,
.card-serie:hover img {
  opacity: 0.3;
  // -webkit-animation: 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  // animation: 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}
.card-movie:hover .card-info,
.card-serie:hover .card-info {
  display: block;
  color: white;
  cursor: pointer;
  text-align: left;
}
</style>
