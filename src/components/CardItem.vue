<template>
  <div>
    <ul>
      <li>{{ title || name }}</li>
      <li>{{ original || originalname }}</li>
      <li v-if="language === 'it'">
        <img src="../assets/img/it.png" alt="italian flag" />
      </li>
      <li v-else-if="language === 'en'">
        <img src="../assets/img/en.png" alt="english flag" />
      </li>
      <li v-else>{{ language }}</li>
      <li>{{ score }}</li>
      <li><img :src="imagesUri + poster" alt="cinematic poster" /></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  data() {
    return {
      imagesUri: "https://image.tmdb.org/t/p/w342",
    };
  },
  props: [
    "title",
    "original",
    "vote",
    "language",
    "originalname",
    "name",
    "poster",
    "series",
    "movies",
  ],
  computed: {
    score() {
      return Math.ceil(this.vote / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>