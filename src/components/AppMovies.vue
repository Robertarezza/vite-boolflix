<script>
export default {
  props: {
    moviedObj: Object,
  },
  data() {
    return {};
  },
  methods: {
    // Metodo per ottenere l'icona della bandiera corrispondente alla lingua
    getLanguageFlagIcon(language) {
      if (!language) return "";
      switch (language.toLowerCase()) {
        case "it":
          console.log("Caricata immagine per lingua italiana");
          return new URL(`../assets/img/it.jpg`, import.meta.url).href;
        case "en":
          return new URL(`../assets/img/en.jpg`, import.meta.url).href;
        case "es":
          return new URL(`../assets/img/es.jpg`, import.meta.url).href;
        case "gl":
          return new URL(`../assets/img/gl.jpg`, import.meta.url).href;
        default:
          return new URL(`../assets/img/mondo.jpg`, import.meta.url).href;
      }
    },
    convertVote(vote) {
      return Math.ceil(vote / 2);
    },
  },
};
</script>

<template>
  <div class="card">
    <span>
      <img
        v-if="moviedObj.poster_path === null && moviedObj.backdrop_path === null"
        class="pellicola"
        src="../assets/img/pellicola.jpg"
        alt=""
      />
      <img
        v-else
        :src="`https://image.tmdb.org/t/p/w342/${moviedObj.poster_path}`"
        alt=""
      />
    </span>
    <h1 v-if="moviedObj.title">{{ moviedObj.title }}</h1>
    <h1 v-else>{{ moviedObj.name }}</h1>
    <h2>{{ moviedObj.original_title }}</h2>
    <img :src="getLanguageFlagIcon(moviedObj.original_language)" class="lang" alt="" />
    <h4>
      <i v-for="index in 5" 
      :class="{ 'star-filled': index <= Math.ceil(moviedObj.vote_average / 2) }"
       class="fa-solid fa-star"></i>
      <!-- Voto: {{ convertVote(moviedObj.vote_average) }} -->
    </h4>
  </div>
 
</template>

<style lang="scss" scoped>

.card{
    background-color: black;
    color:white;

.lang {
  width: 25%;
}
.pellicola {
  width: 100%;
}

.fa-solid {
    color:white;
    border: 1px solid black;
}
.star-filled {
        color: yellow;
    }
}
</style>
