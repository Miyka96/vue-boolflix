<template>
  <main>
    <!-- FILM -->
    <div class="card" v-for="el in arrayFilm" :key="el.id">
      <img
        :class="el.poster_path == null ? 'null' : ''"
        :src="`https://image.tmdb.org/t/p/w300${el.poster_path}`"
      />

      <div class="card-description">
        <h4 id="title">
          Titolo: <span>{{ el.title }}</span>
        </h4>
        <h4 id="title-original">
          Titolo originale: <span>{{ el.original_title }}</span>
        </h4>

        <p v-if="el.original_language == 'it'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1ee-1f1f9.png"
            alt=""
          />
        </p>
        <p v-else-if="el.original_language == 'en'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1ec-1f1e7.png"
            alt=""
          />
        </p>
        <p v-else-if="el.original_language == 'fr'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1eb-1f1f7.png"
            alt=""
          />
        </p>
        <p v-else-if="el.original_language == 'de'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1e9-1f1ea.png"
            alt=""
          />
        </p>

        <p v-else id="langage">Language: {{ el.original_language }}</p>

        <div class="star-wrapper">
          <p v-for="(element, i) in 5" :key="i">
            <span id="starf" v-if="i < stars(el)"> &starf; </span>
            <span id="star" v-else> &star; </span>
          </p>
        </div>
        <br />
        <div class="overview">
          <p>{{ el.overview }}</p>
        </div>
      </div>
    </div>

    <!-- SERIE TV -->

    <div class="card" v-for="el in tvArray" :key="el.id">
      <img
        :class="el.poster_path == null ? 'null' : ''"
        :src="`https://image.tmdb.org/t/p/w300${el.poster_path}`"
      />

      <div class="card-description">
        <h4 id="title">
          Titolo: <span>{{ el.name }}</span>
        </h4>
        <h4 id="title-original">
          Titolo originale: <span>{{ el.original_name }}</span>
        </h4>

        <p v-if="el.original_language == 'it'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1ee-1f1f9.png"
            alt=""
          />
        </p>
        <p v-else-if="el.original_language == 'en'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1ec-1f1e7.png"
            alt=""
          />
        </p>
        <p v-else-if="el.original_language == 'fr'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1eb-1f1f7.png"
            alt=""
          />
        </p>
        <p v-else-if="el.original_language == 'de'" id="langage">
          <img
            id="flag"
            src="https://images.emojiterra.com/google/noto-emoji/v2.034/512px/1f1e9-1f1ea.png"
            alt=""
          />
        </p>

        <p v-else id="langage">Language: {{ el.original_language }}</p>

        <div class="star-wrapper">
          <p v-for="(element, i) in 5" :key="i">
            <span id="starf" v-if="i < stars(el)"> &starf; </span>
            <span id="star" v-else> &star; </span>
          </p>
        </div>
        <br />
        <div class="overview">
          <p>{{ el.overview }}</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "MainVue",
  props: {
    arrayFilm: {
      type: Object,
      required: true,
    },
    tvArray: {
      type: Object,
      required: true,
    },
  },
  methods: {
    stars: function (element) {
      return Math.ceil(element.vote_average / 2);
    },
  },
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
    width: 250px;
    gap: 10px;
    margin-bottom: 40px;
    position: relative;
    transition: all 0.5s ease-in;

    & img {
      display: block;
      width: 100%;
      height: auto;
      object-fit: cover;
    }

    .card-description {
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      height: 100%;
      width: 100%;
      opacity: 0;
      visibility: visible;
      transition: 0.5s ease;
      background-color: black;
      color: white;
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding-left: 10px;
      padding-right: 10px;

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

      #flag {
        height: 20px;
      }
    }
  }
}

.star-wrapper {
  display: flex;
  padding-bottom: 20px;
}

#star {
  color: rgb(233, 233, 147);
}

#starf {
  color: rgb(255, 255, 59);
}

.card:hover .card-description {
  opacity: 0.8;
}

#flag {
  width: 30px;
  height: 15px;
}

.overview {
  overflow-y: auto;
}

.null::before{
  content: "Anteprima immagine non disponibile";
  color: rgba(255, 255, 255, 0.281);
  font-weight: bolder;
}
</style>
