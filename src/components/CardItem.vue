<template>
  <div>
    <ul v-for="item in items" :key="item.id">
      <li>{{ item.title }}</li>
      <li>{{ item.original_title }}</li>
      <li>{{ item.original_language }}</li>
      <li>{{ item.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
</style>