<template>
  <div class="bg-dark p-5">
    <div class="container-lg">
      <div class="row black">
        <div class="col-12">
          <h2>MOVIES</h2>
          <div
            class="card bg-transparent"
            v-for="(movie, i) in movies"
            :key="i"
          >
            <div class="card-body">
              <h3 class="card-title text-secondary">{{ movie.title }}</h3>
              <h4>{{ movie.original_title }}</h4>
              <p class="card-text">
                {{ movie.orginal_language }}
              </p>
            </div>
          </div>
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

<style></style>
