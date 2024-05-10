<script >
import axios from "axios";
import { store } from "./store";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import AppTemp from "./components/AppTemp.vue";

export default {
  components: {
    AppHeader,
    AppMain,
    AppTemp,
  },
  data() {
    return {
     
      store,
      isLoading: true,
    };
  },
  methods: {
    getData() {
        this.getMovie();
        this.getTv();
      },

      searchTv() {
      console.log("fatto");
      axios
        .get("https://api.themoviedb.org/3/search/tv?api_key=a2493a63d1f1247edf82ea1f6793fb71&query=a")
        .then((resp) => {
          console.log(resp);
          this.store.tvArrey = resp.data.results;
          console.log(resp.data.results);
        })
        .catch((error) => {
           console.log(error);
         })
         .finally(() => {
           this.isLoading = false; 
         });
    },
    searchFilms() {
      console.log("fatto");
      axios
        .get("https://api.themoviedb.org/3/search/movie?api_key=a2493a63d1f1247edf82ea1f6793fb71&query=a")
        .then((resp) => {
          console.log(resp);
          this.store.tvArrey = resp.data.results;
          console.log(resp.data.results);
        })
        .catch((error) => {
           console.log(error);
         })
         .finally(() => {
           this.isLoading = false; 
         });
    },
  
    getMovie() {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: this.store.api_Key,
            query: this.store.selectedMovies,
          }
        })
        .then((resp) => {
          console.log(resp);
          this.store.movieArrey = resp.data.results;
        })
        .catch((error) => {
          console.log(error);
        })
        .finally(() => {
          this.isLoading = false; 
        });
    },
    getTv() {
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: this.store.api_Key,
            query: this.store.selectedMovies,
          },
        })
        .then((resp) => {
          console.log(resp);
          this.store.tvArrey = resp.data.results;
          console.log(resp.data.results);
        })
        .catch((error) => {
          console.log(error);
        })
        .finally(() => {
          this.isLoading = false; 
        });
    },
    
  }
};

</script>

<template>
<AppHeader  @cerca="getData" @searchTv="searchTv" @searchmovie="searchFilms" />
<AppMain v-if="!isLoading" />
<AppTemp v-else/>
</template>
<style lang="scss">


</style>
