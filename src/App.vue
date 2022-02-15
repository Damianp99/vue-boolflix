<template>
  <div>
    <Header />
    <Main />
    <Search @search="apiMovies" />
  </div>
</template>

<script>
import axios from "axios";
import Search from "./components/Search.vue";

export default {
  name: "App",
  data() {
    return {
      series: [],
      movies: [],
      api_key: "8d3e931d54a81efc0361bd77f5b9b04a",
      query: "",
    };
  },
  components: {
    Search,
  },
  methods: {
    apiMovies(term) {
      // const config = {
      //   params: {
      //     language: "it-IT",
      //     api_key: this.api_key,
      //     query: term,
      //   },
      // };
      console.log(term);
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=8d3e931d54a81efc0361bd77f5b9b04a&language=it_IT&query=games"
        )
        .then((res) => {
          this.movies = res.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
