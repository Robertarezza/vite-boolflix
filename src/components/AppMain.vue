<script >

import { store } from "../store";


export default {
  
  data() {
    return {
     store,
   
    };
  },
  methods: {
    // Metodo per ottenere l'icona della bandiera corrispondente alla lingua
    getLanguageFlagIcon(language) {
      if (!language) return "";
      switch (language.toLowerCase()) {
        case 'it':
        console.log("Caricata immagine per lingua italiana");
        return new URL(`../assets/img/it.jpg`, import.meta.url).href;
        case 'en':
          return new URL(`../assets/img/en.jpg`, import.meta.url).href;
        case 'es':
          return new URL(`../assets/img/es.jpg`, import.meta.url).href;
          case 'gl':
          return new URL(`../assets/img/gl.jpg`, import.meta.url).href;
        default:
          return new URL(`../assets/img/mondo.jpg`, import.meta.url).href;
      }
    },
  },
  
 
 
};

</script>

<template>
<main>
  <div class="container mt-5">
    <div class="row row-cols-4">
      <div class="col mb-4" v-for="movie in store.movieArrey"  >
      <div class="card">
        <h1> {{movie.title}}</h1>
        <h2> {{movie.original_title}} </h2>
        <img :src="getLanguageFlagIcon(movie.original_language)" alt="">
        <h4>Voto: {{movie.vote_average}}</h4>
      </div>
      </div>
    </div>
  </div>
</main>
</template>

<style lang="scss" scoped>
img{
  width: 25%;
}

</style>
