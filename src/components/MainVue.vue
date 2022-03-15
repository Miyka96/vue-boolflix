<template>
  <main>
    <div class="card"  v-for="el in arrayFilm" :key="el.id">
      <div class="card-thumb"></div>

      <div class="card-description">
        <h4 id="title">Titolo: <span>{{ el.title}}</span></h4>
        <h4 id="title-original">
          Titolo originale: <span>{{el.original_title}}</span>
        </h4>
        <p id="langage">{{el.original_language}}</p>
        <p id="vote">{{el.vote_average}}/10</p>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainVue",
  props: {
    arrayFilm:{
      type: Object,
      required: true,
    }
  }
};
</script>

<style lang="scss" scoped>
main {
  width: 100%;
  flex-grow: 1;
  background-color: rgb(27, 27, 27);
  overflow-y: auto;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  flex-wrap: wrap;
  padding: 40px;
  gap: 20px;

  .card {
    width: calc(100% / 6);
    aspect-ratio: 1/2;

    display: flex;
    flex-direction: column;
    padding: 5px;
    gap: 10px;

    .card-thumb {
      flex-grow: 1;
      border: 1px solid white;
    }

    .card-description {
      color: white;

      & span {
        color: white;
        font-weight: 100;
      }

      & h4 {
        font-weight: 900;
      }

      & p {
        font-size: 14px;
      }
    }
  }
}
</style>
