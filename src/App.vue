<template>
  <div>
    <Search @search="getApiItems" />
    <div v-for="item in items" :key="item.id">
      <CardItem
        :title="item.title"
        :original="item.original_title"
        :language="item.original_language"
        :vote="item.vote_average"
      />
    </div>
    <div v-for="item in items" :key="item.id">
      <CardItem
        :name="item.name"
        :originalname="item.original_name"
        :language="item.original_language"
        :vote="item.vote_average"
      />
    </div>
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
      items: [],
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
          this.items = res.data.results;
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
        .then((res2) => {
          this.items = res2.data.results;
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
