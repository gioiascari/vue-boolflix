<template>
  <div id="app">
    <!-- HEADER -->
    <MyHeader @searchArguments="getMovie" />
    <!-- /HEADER -->

    <MyMain :movies="movies" />
  </div>
</template>

<script>
import axios from "axios";
import MyHeader from "./components/myHeader.vue";
import MyMain from "@/components/MyMain.vue";

export default {
  name: "App",
  components: {
    MyMain,
    MyHeader,
  },

  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "20dc8cd40c372b121bcf70b5be101585",
      query: "",
      series: [],
      movies: [],
    };
  },
  methods: {
    //Movies
    getMovie() {
      const params = {
        api_key: this.apiKey,
        query: this.query,
        language: "it-IT",
      };
      axios.get(this.apiUrl + "movie", { params: params }).then((res) => {
        this.movies = res.data.results;
        console.log(this.movies);
      });
    },
  },
};
</script>

<style lang="scss">
@import "@/style/utilities";

#app {
  font-family: "Bebas Neue", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
