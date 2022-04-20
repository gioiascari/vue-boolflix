<template>
  <div id="app">
    <MyHeader @searching="searchArguments" />
    <MyMain />
    <!-- <input type="text" v-model="query" />
    <button @click="searchArguments">Cerca</button>
    <div v-for="item in series" :key="item.id">{{ item.name }}</div>
    <div v-for="item in films" :key="item.id">{{ item.name }}</div> -->
  </div>
</template>

<script>
import axios from "axios";
import MyHeader from "./components/MyHeader.vue";
import MyMain from "./components/MyMain.vue";

export default {
  name: "App",
  components: {
    MyMain,
    MyHeader,
  },

  data() {
    return {
      apiKey: "20dc8cd40c372b121bcf70b5be101585",
      apiUrl: "https://api.themoviedb.org/3/search/",
      query: "",
      searching: false,
      series: [],
      films: [],
    };
  },
  methods: {
    searchArguments() {
      if (!this.searching && this.query.length > 0) {
        this.queryApi("tv").then((response) => {
          this.searching = false;
          this.series = response.data.results;
        });
        this.queryApi("movie").then((response) => {
          this.searching = false;
          this.films = response.data.results;
        });
      }
    },

    //General API
    querySeriesApi() {
      this.queryApi("tv");
    },
    queryMovieApi() {
      this.queryApi("movie");
    },

    queryApi(searchFolder) {
      this.searching = true;

      //Richiesta API tramite funzione
      const params = {
        query: this.query,
        api_key: this.apiKey,
        language: "it-IT",
      };
      //Axios
      return axios
        .get(this.apiUrl + searchFolder, { params })
        .catch((error) => {
          console.log(error);
          this.searching = false;
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
  margin-top: 60px;
}
</style>
