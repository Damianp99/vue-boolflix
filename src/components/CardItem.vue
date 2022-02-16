<template>
  <div>
    <ul>
      <li>{{ title || name }}</li>
      <li>{{ original || originalname }}</li>
      <li>{{ language }}</li>
      <li>{{ vote }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: ["title", "original", "vote", "language", "originalname", "name"],
};
</script>

<style lang="scss" scoped>
</style>