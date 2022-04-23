<template>
  <div class="container-fluid">
    <!-- Trending movies -->
    <div class="row">
      <h2 class="text-danger p-4 m-0 p-3">Movies</h2>
      <div class="col-12 d-flex flex-wrap justify-content-between">
        <div
          class="card-movie bg-transparent w_20"
          v-for="(item, i) in trendingMovies"
          :key="i"
        >
          <img
            class="cover card-image"
            v-if="item.poster_path != null"
            :src="'https://image.tmdb.org/t/p/w342' + item.poster_path"
            alt="cover-movie"
          />
          <img
            class="cover card-image"
            v-else
            src="https://www.altavod.com/assets/images/poster-placeholder.png"
            alt="cover-movie"
          />
          <div class="card-info">
            <h3 class="card-title text-white fs-5">
              Title:
              {{ item.title }}
            </h3>
            <h4 class="text-danger">
              Original title: {{ item.original_title }}
            </h4>
            <p class="card-text">
              {{ item.original_language }}

              <lang-flag :iso="item.original_language" />
            </p>

            <div class="star_rating">
              <p>
                Voto:
                <star-rating
                  :inline="true"
                  :star-size="20"
                  :read-only="true"
                  :show-rating="false"
                  v-bind:max-rating="Math.round(item.vote_average / 2)"
                  inactive-color="#ffff00"
                >
                </star-rating>
              </p>
            </div>
            <div>
              <span>Overview : {{ item.overview }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- /Trending movies -->
    <!-- Trending Series -->
    <div class="row">
      <h2 class="text-danger p-4 m-0 p-3">TV Series</h2>
      <div class="col-12 d-flex flex-wrap justify-content-between">
        <div
          class="card-movie bg-transparent w_20"
          v-for="(item, i) in trendingTV"
          :key="i"
        >
          <img
            class="cover card-image"
            v-if="item.poster_path != null"
            :src="'https://image.tmdb.org/t/p/w342' + item.poster_path"
            alt="cover-movie"
          />
          <img
            class="cover card-image"
            v-else
            src="https://www.altavod.com/assets/images/poster-placeholder.png"
            alt="cover-movie"
          />
          <div class="card-info">
            <h3 class="card-title text-white fs-5">
              Title:
              {{ item.title }}
            </h3>
            <h4 class="text-danger">
              Original title: {{ item.original_title }}
            </h4>
            <p class="card-text">
              {{ item.original_language }}

              <lang-flag :iso="item.original_language" />
            </p>

            <div class="star_rating">
              <p>
                Voto:
                <star-rating
                  :inline="true"
                  :star-size="20"
                  :read-only="true"
                  :show-rating="false"
                  v-bind:max-rating="Math.round(item.vote_average / 2)"
                  inactive-color="#ffff00"
                >
                </star-rating>
              </p>
            </div>
            <div>
              <span>Overview : {{ item.overview }}</span>
            </div>
            <div>
              <span>Actors : {{ item.overview }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- /rending Series -->
  </div>
</template>

<script>
// adult: false
// backdrop_path: (...)
// genre_ids: (...)
// id: (...)
// media_type: (...)
// original_language: (...)
// original_title: (...)
// overview: (...)
// popularity: (...)
// poster_path: (...)
// release_date: (...)
// title: "Spider-Man: No Way Home"
// video: false
// vote_average: (...)
// vote_count: (...)
export default {
  name: "HomeCards",
  props: {
    trendingMovies: Array,
    trendingTV: Array,
  },
  data() {
    return {
      urlMovie: "https://api.themoviedb.org/3/movie/",
    };
  },

  methods: {},
};
</script>

<style scoped lang="scss">
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
}
.card-movie:hover .card-info,
.card-serie:hover .card-info {
  display: block;
  color: white;
  cursor: pointer;
  text-align: left;
}
</style>
