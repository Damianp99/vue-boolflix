<template>
  <div>
    <input
      type="text"
      placeholder="Cerca..."
      v-model.trim="word"
      @keyup.enter="search"
    />
    <button @click="search">Cerca</button>
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

<style>
</style>