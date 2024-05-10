<script>
import { store } from "../store";
import AppMovies from "./AppMovies.vue";
import AppTv from "./AppTv.vue";
import AppFilms from "./AppFilms.vue";

export default {
  components: {
    AppMovies,
    AppTv,
    AppFilms,
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
    <div class="container pt-5">
      <h1 class="title">Film</h1>
      <div class="row row-cols-4 pb-5"> 
        <div class="col mb-4" v-for="movie in store.movieArrey">
          <AppMovies :moviedObj="movie"/>
        </div>
        <div class="col mb-4" v-for="movie in store.movieArrey">
          <AppFilms :moviedObj="movie"/>
         
        </div>
      </div>
      <h1 class="title">Serie Tv</h1>
      <div class="row row-cols-4">
        <div class="col mb-4" v-for="tv in store.tvArrey">
          <AppMovies :moviedObj="tv"/>
        </div> 
        <div class="col mb-4" v-for="tv in store.tvArrey">
          <AppTv :moviedObj="tv" />
        </div>
        
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main{
  background-image: url(../assets/img/sfondo.png);

  .title {
    font-size: 3rem;
    font-weight: 800;
    color:black;
  }

}
</style>
