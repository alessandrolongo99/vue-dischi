<template>
  <div>
    <img :src="imgSrc" :alt="title" />
    <h3 class="text-uppercase">{{ title }}</h3>
    <span>{{ artist }}</span>
    <span>{{ year }}</span>
  </div>
</template>

<script>
export default {
  props: {
    imgSrc: String,
    title: String,
    artist: String,
    year: Number,
  },
};
</script>

<style scoped>
div {
  background-color: #2e3a46;
  width: calc(100% / 5 - 2rem);
  padding: 1rem;
}

img {
  width: 100%;
  margin: 1rem;
  object-fit: cover;
  object-position: top;
}

span {
  color: #6c787e;
}
</style>