<template>
  <div id="app">
    <SearchNav @film="filmFunction" @tv='tvFunction' />
    <Main-vue :arrayFilm="temporaryArray" :tvArray="tvTemporaryArray" />
  </div>
</template>

<script>
import MainVue from "./components/MainVue.vue";
import SearchNav from "./components/SearchNav.vue";

export default {
  name: "App",
  components: {
    MainVue,
    SearchNav,
  },

  data() {
    return {
      temporaryArray: {},
      tvTemporaryArray: {},
    };
  },

  methods: {
    filmFunction: function(filmArray){
      this.temporaryArray = filmArray;
    },
    tvFunction: function(tvArray){
      this.tvTemporaryArray = tvArray;
    }
  }

};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Signika:wght@300&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Signika", sans-serif;
}

#app {
  width: 100%;
  height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
