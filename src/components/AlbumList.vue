<template>
  <div class="text-white">
    <AppAlbum v-for="(album, index) in albums" :key="index"
    :imgSrc="album.poster"/>
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