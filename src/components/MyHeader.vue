<template>
  <div class="bg-dark p-5">
    <div class="container-lg">
      <div class="row">
        <div class="col-12 d-flex justify-content-around">
          <h1 class="text-danger">BoolFlix</h1>

          <ul class="d-flex">
            <li><a class="mx-2 text-light" href="">Home</a></li>
            <li><a class="mx-2 text-light" href="serie">Serie Tv</a></li>
            <li><a class="mx-2 text-light" href="film">Films</a></li>
            <li><a class="mx-2 text-light" href="">La mia lista</a></li>
          </ul>
          <div class="d-flex">
            <div>
              <input
                v-model="searchMovie"
                @keyup.enter="startSearch"
                type="text"
              />
            </div>
            <div>
              <button
                type="button"
                @click.prevent="startSearch"
                class="btn bg-danger bg-gradient mx-3"
              >
                Cerca film
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyHeader",
  data() {
    return {
      searchMovie: "",
    };
  },
  methods: {
    startSearch() {
      this.$emit("searchArguments", this.searchMovie);
      console.log(this.searchMovie);
    },
  },
};
</script>

<style lang="scss">
@import "@/style/utilities";
</style>
