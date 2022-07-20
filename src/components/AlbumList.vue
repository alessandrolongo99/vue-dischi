<template>
  <div class="row text-white justify-content-between g-4">
    <loader
      v-show="isLoading"
      object="#ff9633"
      color1="#ffffff"
      color2="#17fd3d"
      size="5"
      speed="2"
      bg="#343a40"
      objectbg="#999793"
      opacity="80"
      name="circular"
    ></loader>
    <div>
      <select class="form-select my-3" aria-label="Default select example">
        <option selected>Open this select menu</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>
      <select class="form-select my-3" aria-label="Default select example">
        <option selected>Open this select menu</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select>
    </div>
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
      isLoading: true,
    };
  },
  methods: {
    getAlbum() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((result) => {
          this.albums = result.data.response;
          this.isLoading = false;
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