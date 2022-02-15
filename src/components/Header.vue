<template>
  <div>
    <Search placeholder="Cerca un film" @search="searchItem" />
  </div>
</template>

<script>
import Search from "./Search.vue";
export default {
  name: "Header",

  data() {
    return {};
  },
  components: {
    Search,
  },
  methods: {
    searchItem(word) {},
  },
};
</script>

<style>
</style>