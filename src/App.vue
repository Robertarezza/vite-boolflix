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
     searchCompleat: false,
      store,
    };
  },
  methods: {
  getSearch() {
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

      
        return axios.get("https://api.themoviedb.org/3/search/tv", {
          params: {
            api_key: this.store.api_Key,
            query: this.store.selectedMovies,
          }
        });
      })
      .then((resp) => {
        console.log(resp);
        this.store.tvArrey = resp.data.results;
        this.searchCompleat = true,
        console.log(resp.data.results);
       
      })
     
  }
}
 
 
};

</script>

<template>
<AppHeader  @cerca="getSearch"/>
<AppMain v-if="searchCompleat" />
<AppTemp v-else/>
</template>

<style lang="scss">


</style>
