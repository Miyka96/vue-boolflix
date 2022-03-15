<template>
  <main>
    <div class="card">

      <div class="card-thumb"></div>

      <div class="card-description">
        <h4 id="title"> Titolo: <span>Pierino</span></h4>
        <h4 id="title-original"> Titolo originale: <span>Pierino al mare</span></h4>
        <p id="langage">Italo-americano</p>
        <p id="vote">Voto: 44/10</p>

      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainVue",
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
  justify-content: center;
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

    .card-thumb{
        flex-grow: 1;
        border: 1px solid white;
    }

    .card-description{
        color: white;
    }
  }
}
</style>
