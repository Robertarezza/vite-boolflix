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
    <div class="container pt-5">
      <h1 class="title">Film</h1>
      <div class="row row-cols-4 pb-5"> 
        <div class="col mb-4" v-for="movie in store.movieArrey">
          <AppMovies :moviedObj="movie"/>
        </div>
      </div>
      <h1 class="title">Serie Tv</h1>
      <div class="row row-cols-4">
        <div class="col mb-4" v-for="tv in store.tvArrey">
          <AppMovies :moviedObj="tv"/>
        </div> 
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
main{
  background-color: grey;

  .title {
    font-size: 3rem;
    font-weight: 800;
  }

}
</style>
