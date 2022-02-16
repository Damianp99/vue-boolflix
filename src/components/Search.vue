<template>
  <div class="d-flex mx-4">
    <input
      class="form-control"
      type="text"
      placeholder="Cerca..."
      v-model.trim="word"
      @keyup.enter="search"
    />
    <button class="btn btn-danger mx-3" @click="search">Cerca</button>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      word: "",
    };
  },
  methods: {
    search() {
      this.$emit("search", this.word);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/style.scss";
</style>