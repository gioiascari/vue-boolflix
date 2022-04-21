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
import MyHeader from "./components/MyHeader.vue";
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
      series: [],
      movies: [],
    };
  },
  methods: {
    //Movies
    getMovie(query) {
      if (query.length > 0) {
        console.log({ query });
        const url = this.apiUrl + "movie";
        const config = {
          params: {
            api_key: "20dc8cd40c372b121bcf70b5be101585",
            query,
            language: "it-IT",
          },
        };
        axios.get(url, config).then((res) => {
          console.log({ res });
          this.movies = res.data.results;
          console.log(this.movies);
        });
      }
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
