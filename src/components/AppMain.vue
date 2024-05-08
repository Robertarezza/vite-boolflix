<script >

import { store } from "../store";


export default {
  
  data() {
    return {
     store,
   
    };
  },

 
 
};

</script>

<template>
<main>
  <div class="container mt-5">
    <div class="row row-cols-4">
      <div class="col mb-4" v-for="movie in store.movieArrey"  >
        <h1>Titolo: {{movie.title}}</h1>
        <h2>Titolo Originale: {{movie.original_title}}</h2>
        <h3>Lingua Orgiginale:{{movie.original_language}}</h3>
        <h4>Voto: {{movie.vote_average}}</h4>
      </div>
    </div>
  </div>
</main>
</template>

<style lang="scss" scoped>

</style>
