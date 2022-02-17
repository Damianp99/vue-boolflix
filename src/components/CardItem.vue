<template>
  <div class="container text-white">
    <div>
      <div
        class="card-item d-flex align-items-center"
        :style="{
          backgroundImage: 'url(' + imagesUri + poster + ')',
          backgroundPosition: 'center center',
          backgroundSize: 'cover',
          backgroundRepeat: 'no-repeat',
        }"
      >
        <ul class="list-unstyled">
          <li>{{ title || name }}</li>
          <li>{{ original || originalname }}</li>
          <li v-if="language === 'it'">
            <img class="flag" src="../assets/img/it.png" alt="italian flag" />
          </li>
          <li v-else-if="language === 'en'">
            <img class="flag" src="../assets/img/en.png" alt="english flag" />
          </li>
          <li v-else>{{ language }}</li>
          <li>
            <strong><span>VOTO:</span></strong>
            <i
              v-for="star in 5"
              :key="star"
              class="fa-star"
              :class="star <= score ? 'fa-solid' : 'fa-regular'"
            ></i>
          </li>
          <li class="">{{ overview }}</li>
          <li class="poster">
            <!-- <img :src="imagesUri + poster" alt="cinematic poster" /> -->
          </li>
        </ul>
      </div>
    </div>
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
    "overview",
  ],
  computed: {
    score() {
      return Math.ceil(this.vote / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/style.scss";
.card-item {
  overflow-y: auto;
  width: 342px;
  height: 513px;
  margin-bottom: 30px;
}
ul {
  li {
  }
}
.poster {
  position: relative;
}
.flag {
  width: 50px;
}
</style>