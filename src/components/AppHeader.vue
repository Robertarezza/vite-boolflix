<script>
import { store } from "../store";
export default {
  //per evitare warning
  emits: ["cerca","searchTv"],
  data() {
    return {
      store,
    };
  },
  
};
</script>

<template>
  <header>
    <div
      class="container d-flex justify-content-between align-items-center pt-4 ps-3 pe-5 pb-4"
    >
      <div class="cont-dx">
        <h1>BOOLFLIX</h1>
        <ul>
          <li @click="$emit('searchmovie')">Film</li>
          <li @click="$emit('searchTv')">Serie Tv</li>
        </ul>
      </div>
      <div>
        <input
          type="text"
          name=""
          aria-label="inizia la ricerca"
          v-model="store.selectedMovies"
          placeholder="Search"
          @keydown.enter="$emit('cerca')"
        />
        <!-- <button type="cerca"  >clicca</button> -->
      </div>
    </div>
  </header>
</template>

<style lang="scss" scoped>
header {
  background-color: black;

  .cont-dx {
    display: flex;
    align-items: center;
  }
  ul{
    list-style-type: none;
    li{
      color: white;
      cursor: pointer;
    }
  }

  h1 {
    color: red;
  }
}
</style>
