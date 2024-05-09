<script>
import { store } from "../store";
import AppMovies from "./AppMovies.vue";

export default {
  components: {
    AppMovies,
  },
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
      <h1>Film</h1>
      <div class="row row-cols-4"> 
        <div class="col mb-4" v-for="movie in store.movieArrey">
          
          <AppMovies :moviedObj="movie"/>
        </div>
      </div>
      <h1>Serie Tv</h1>
      <div class="row row-cols-4">
        <div class="col mb-4" v-for="movie in store.tvArrey">
          <AppMovies :moviedObj="movie"/>
        </div> 
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main{
  background-color: black;
  
}
</style>
