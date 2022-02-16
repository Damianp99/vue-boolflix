<template>
  <div class="text-center">
    <header class="p-4 d-flex justify-content-between align-items-center">
      <h1 class="text-danger">BOOLFIX</h1>
      <div class="mx-5">
        <Search @search="getApiItems" />
      </div>
    </header>
    <main>
      <div class="container">
        <h2>MOVIES</h2>
        <div class="row">
          <div v-for="movie in movies" :key="movie.id" class="col-4">
            <CardItem
              :title="movie.title"
              :original="movie.original_title"
              :language="movie.original_language"
              :vote="movie.vote_average"
              :overview="movie.overview"
              :poster="movie.poster_path"
            />
          </div>
        </div>
      </div>
      <div class="container">
        <h2>SERIES</h2>
        <div class="row">
          <div v-for="serie in series" :key="serie.id" class="col-4">
            <CardItem
              :name="serie.name"
              :originalname="serie.original_name"
              :language="serie.original_language"
              :vote="serie.vote_average"
              :overview="serie.overview"
              :poster="serie.poster_path"
            />
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Search from "./components/Search.vue";
import CardItem from "./components/CardItem.vue";

export default {
  name: "App",
  data() {
    return {
      series: [],
      movies: [],
      api_key: "cfc0856a6e486ed1f7367bd371b61e4e",
      query: "",
    };
  },
  components: {
    CardItem,
    Search,
  },
  props: [],
  methods: {
    apiMovies(term) {
      if (!term) {
        return;
      }
      const config = {
        params: {
          language: "it-IT",
          api_key: this.api_key,
          query: term,
        },
      };
      console.log(term);
      console.log(
        "https://api.themoviedb.org/3/search/movie?api_key=cfc0856a6e486ed1f7367bd371b61e4e&query=games"
      );
      axios
        .get("https://api.themoviedb.org/3/search/movie", config)
        .then((res) => {
          this.movies = res.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    apiSeries(term) {
      if (!term) {
        return;
      }
      const config = {
        params: {
          language: "it-IT",
          api_key: this.api_key,
          query: term,
        },
      };
      console.log(term);
      console.log(
        "https://api.themoviedb.org/3/search/movie?api_key=cfc0856a6e486ed1f7367bd371b61e4e&query=games"
      );
      axios
        .get("https://api.themoviedb.org/3/search/tv", config)
        .then((res) => {
          this.series = res.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    getApiItems(term) {
      this.query = term;
      this.apiSeries(term);
      this.apiMovies(term);
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
