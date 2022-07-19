<template>
  <div>
    <img :src="imgSrc" alt="title">
  </div>
</template>

<script>
export default {
    props: {
        imgSrc: String,
        title: String,
        artist: String,
        year: Number,
    }
}
</script>

<style>

</style>