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
      <select
        v-model="selectedGenre"
        @change="filterGenre"
        class="form-select my-3"
        aria-label="Default select example"
      >
        <option value="all">Genere</option>
        <option v-for="(genre, index) in genres" :key="index" :value="genre">
          {{ genre }}
        </option>
      </select>
      <!-- <select class="form-select my-3" aria-label="Default select example">
        <option disabled value="">Open this select menu</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
      </select> -->
    </div>
    <AppAlbum
      class="
        d-flex
        flex-column
        justify-content-start
        align-items-center
        text-center
      "
      v-for="(album, index) in filteredAlbums"
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
      filteredAlbums: [],
      genres: [],
      selectedGenre: "",
      isLoading: true,
    };
  },
  methods: {
    getAlbum() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((result) => {
          this.albums = result.data.response;
          this.filteredAlbums = [...this.albums];
          this.isLoading = false;
          this.getGenres();
        })
        .catch((error) => {
          console.warn(error);
        });
    },
    getGenres() {
      for (let i = 0; i < this.albums.length; i++) {
        if (!this.genres.includes(this.albums[i].genre)) {
          this.genres.push(this.albums[i].genre);
        }
      }
    },
    filterGenre(){
      if(!(this.selectedGenre == 'all')){
        this.filteredAlbums = this.albums.filter((album) => {
          return album.genre == this.selectedGenre;
        })
        console.log(this.filteredAlbums)
      } else{
        this.filteredAlbums = [...this.albums];
        console.log(this.filteredAlbums)
      }
    },
  },
  created() {
    this.getAlbum();
  },
};
</script>

<style>
</style>