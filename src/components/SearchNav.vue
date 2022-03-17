<template>
  <nav>
    <img id="logo" src="..\src\assets\img\Boolflix.svg" alt="">
    <div id="search">
      <input
        type="search"
        id="search-bar"
        v-model="search"
        @keyup.enter="searchItems"
      />
      <button id="search-btn" @click="searchItems">Search</button>
    </div>
  </nav>
</template>

<script>
import axios from "axios";

export default {
  name: "SearchNav",

  data() {
    return {
      baseURL: "https://api.themoviedb.org/3",
      search: "",
      filmArray: [],
      tvArray: [],
    };
  },

  methods: {
    searchItems: function () {
      axios
        .get(`${this.baseURL}/search/movie`, {
          params: {
            api_key: "faa3d25c66c254fa24c269f4b5cf46ff",
            query: this.search,
            language: "it-IT",
          },
        })
        .then((res) => {
          console.log(res.data.results);
          this.filmArray = res.data.results;
          this.$emit("film", this.filmArray);
          this.filmArray = [];
        })
        .catch((error) => {
          console.log(error.response);
        });

      // chiamata per le serie tv

      axios
        .get(`${this.baseURL}/search/tv`, {
          params: {
            api_key: "faa3d25c66c254fa24c269f4b5cf46ff",
            language: "it-IT",
            query: this.search,
          },
        })
        .then((res) => {
          console.log(res.data.results);
          this.tvArray = res.data.results;
          this.$emit("tv", this.tvArray);
          this.tvArray = [];
        })
        .catch((error) => {
          console.log(error.response);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
nav {
  width: 100%;
  height: fit-content;
  background-color: rgb(41, 41, 41);
  display: flex;
  align-items: center;
  justify-content: space-around;
  flex-wrap: wrap;
  padding-bottom: 10px;

  #logo{
    height: 60px;
    padding: 10px 25px;
  }

  #search {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;

    #search-bar {
      min-width: 150px;
      height: 25px;
      border: 1px solid black;
      background-color: grey;
      border-radius: 5000px;

      &:hover,
      &:focus {
        filter: brightness(1.5);
      }
    }

    #search-btn {
      height: 25px;
      border: 1px solid black;
      background-color: rgb(167, 167, 167);
      padding: 0 10px;
      margin: 0 5px;
      cursor: pointer;
      border-radius: 5000px;

      &:hover {
        filter: brightness(1.5);
      }
    }
  }
}
</style>
