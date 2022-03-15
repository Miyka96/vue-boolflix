<template>
  <nav>
    <h1>Boolflix</h1>
    <div id="search">
      <input type="search" id="search-bar" />
      <button id="search-btn">Search</button>
    </div>
  </nav>
</template>

<script>
export default {
  name: "SearchNav",
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

      &:hover, &:focus{
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
