<template>
  <div>
    <Header />
    <Main />
  </div>
</template>

<script>
import axios from "axios";
import Main from "./components/Main.vue";
import Header from "./components/Header.vue";
export default {
  name: "App",
  data() {
    return {
      item: [],
      api_key: "8d3e931d54a81efc0361bd77f5b9b04a",
      query: "games",
    };
  },
  components: {
    Header,
    Main,
  },
  methods: {
    apiCall() {
      const config = {
        params: {
          language: "it-IT",
          api_key: this.api_key,
          query: this.query,
        },
      };
      axios
        .get(`https://api.themoviedb.org/3/search/movie`, config)
        .then((res) => {
          this.item = res.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
</style>
