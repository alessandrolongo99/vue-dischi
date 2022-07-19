<template>
  <main>
    <div class="container">
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
}
</style>