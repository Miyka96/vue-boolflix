<template>
  <nav>
    <h1>Boolflix</h1>
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
          this.$emit('film',this.filmArray);
        })
        .catch((error) => {
          console.log(error.response);
        })

      this.search = "";

      // mo' dovresti pushare nell'array dei film, che poi dovrai stampare sul Main Vue, ricordati anche di RESETTARE la search bar prima di ritrovarti 98759438759387 film nell'array.
    },
  },
};
</script>

<style lang="scss" scoped>
nav {
  width: 100%;
  height: 70px;
  background-color: rgb(41, 41, 41);
  display: flex;
  align-items: center;
  justify-content: space-between;

  h1 {
    color: red;
    font-size: 40px;
    padding: 10px 40px;
    font-weight: 800;
  }

  #search {
    padding: 10px 100px;

    #search-bar {
      min-width: 150px;
      height: 25px;
      border: 1px solid black;
      background-color: grey;

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

      &:hover {
        filter: brightness(1.5);
      }
    }
  }
}
</style>
