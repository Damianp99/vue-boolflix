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
      <li>{{ vote }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: ["title", "original", "vote", "language", "originalname", "name"],
  methods: {
    getItemImg() {},
  },
};
</script>

<style lang="scss" scoped>
</style>