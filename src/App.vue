<script >
import axios from "axios";
import { store } from "./store";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import AppSearch from "./components/AppSearch.vue";

export default {
 
  components: {
    AppHeader,
    AppMain,
    AppSearch,

  },
  data() {
    return {
     
      store,
    };
  },
  methods: {
    getSearch () {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            api_key: this.store.api_Key,
            query: this.store.selectedMovies,

          }
        })
        .then((resp) => {
          console.log(resp);
          this.store.movieArrey = resp.data.results,
          console.log(resp.data.results);
          console.log(resp.data.results.title);
        });
    }
  },

 
 
};

</script>

<template>
<AppHeader />
<AppSearch @cerca="getSearch"/>
<AppMain />
</template>

<style lang="scss">

</style>
