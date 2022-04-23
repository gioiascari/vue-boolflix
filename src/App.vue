<template>
  <div id="app">
    <!-- HEADER -->
    <MyHeader @searchArguments="getAll" />
    <!-- /HEADER -->
    <MyMain
      :movies="movies"
      :series="series"
      :trendingMovies="trendingMovies"
    />
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
      apiTrendingMovie:
        "https://api.themoviedb.org/3/trending/movie/week?api_key=",
      apiTrendingTV: "https://api.themoviedb.org/3/trending/tv/week?api_key=",
      series: [],
      movies: [],
      trendingMovies: [],
      trendingTV: [],
    };
  },
  created() {
    //Utilizzo la funzione 'all' di axios per lavorare su multeplici dati in uno
    axios
      .all([
        axios.get(this.apiTrendingMovie + this.apiKey),
        axios.get(this.apiTrendingTV + this.apiKey),
      ])
      .then(
        axios.spread((resMovieT, resTV) => {
          this.trendingMovies = resMovieT.data.results;
          console.log("Trending", this.trendingMovies);
          this.trendingTV = resTV.data.results;
        })
      )
      .catch((err) => {
        console.log(err);
      });
  },
  methods: {
    // getTrending(text) {
    //   if (text.length <= 0) {
    //     ///Effetuo due chiamate per ricevere i programmi in tendenza
    //     const config = {
    //       params: {
    //         api_key: "20dc8cd40c372b121bcf70b5be101585",
    //         text,
    //         language: "it-IT",
    //       },
    //     };
    //     axios.get(this.apiTrendingMovie, config).then((res) => {
    //       console.log("Trending", { res });
    //       this.trendingMovies = res.data.results;
    //       console.log("Trending Movies", this.trendingMovies);
    //     });
    //   }
    // },
    getAll(query) {
      if (query.length > 0) {
        console.log({ query });
        //Movies
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
          console.log("Movies", this.movies);
        });
        //TV Series
        axios.get(this.apiUrl + "tv", config).then((res) => {
          this.series = res.data.results;
          console.log("SerieTV", this.series);
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
