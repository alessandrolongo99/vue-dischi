<template>
  <div class="row text-white justify-content-between g-4">
    <AppAlbum
      class="
        d-flex
        flex-column
        justify-content-start
        align-items-center
        text-center
      "
      v-for="(album, index) in albums"
      :key="index"
      :imgSrc="album.poster"
      :title="album.title"
      :artist="album.author"
      :year="album.year"
    />
  </div>
</template>

<script>
import axios from "axios";
import AppAlbum from "./AppAlbum.vue";

export default {
  name: "AlbumList",
  components: {
    AppAlbum,
  },
  data: function () {
    return {
      albums: [],
    };
  },
  methods: {
    getAlbum() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((result) => {
          this.albums = result.data.response;
        })
        .catch((error) => {
          console.warn(error);
        });
    },
  },
  created() {
    this.getAlbum();
  },
};
</script>

<style>
</style>