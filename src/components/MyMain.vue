<template>
  <div class="bg-dark p-5 text-light">
    <div class="container-lg text-light">
      <div class="row black">
        <h2 class="text-danger">MOVIES</h2>
        <div class="col-12 d-flex flex-wrap justify-content-center">
          <!-- MOVIES CONTAINER -->

          <div
            class="card bg-transparent w_20"
            v-for="(movie, i) in movies"
            :key="i"
          >
            <img
              class="cover position-relative"
              :src="'https://image.tmdb.org/t/p/w342' + movie.poster_path"
              alt="cover-movie"
            />
            <div class="card-body">
              <h3 class="card-title text-secondary">
                {{ movie.title ? movie.title : movie.name }}
              </h3>
              <h4>{{ movie.original_title }}</h4>
              <p class="card-text">
                {{ movie.original_language }}
              </p>
            </div>
          </div>
          <!--/ MOVIES CONTAINER -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyMain",
  components: {},
  props: {
    movies: Array,
  },
};
</script>

<style>
.w_20 {
  width: 20rem;
}
</style>
