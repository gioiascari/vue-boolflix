<template>
  <div class="container">
    <div v-if="!trendingMovies > 0">LOL</div>
  </div>
</template>

<script>
export default {
  name: "HomeCards",
  props: {
    trendingMovies: Array,
  },
};
</script>

<style></style>
