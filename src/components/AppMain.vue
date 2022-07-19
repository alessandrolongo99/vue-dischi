<template>
  <main>
    <div class="container py-5">
      <AlbumList />
    </div>
  </main>
</template>

<script>
import AlbumList from "./AlbumList.vue";

export default {
  name: "AppMain",
  components: {
    AlbumList,
  },
};
</script>

<style scoped>
main {
  background-color: #1e2d3b;
  height: 100%;
}
</style>