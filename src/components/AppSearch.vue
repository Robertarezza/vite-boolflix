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
   <div>
    <input type="cerca" name=""  v-model="store.selectedMovies"  >
    <button type="cerca" @click="$emit('cerca')" >clicca</button>
   </div>

</template>

<style lang="scss" scoped>

</style>