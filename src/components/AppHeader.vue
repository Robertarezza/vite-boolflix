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
  <header>
  <div class=" container d-flex justify-content-between align-items-center pt-4 ps-3 pe-5 pb-4"> 
  <div>
    <h1>BOOLFLIX</h1>
  </div>
   <div>
    <input type="cerca" name=""  v-model="store.selectedMovies" @keydown.enter="$emit('cerca')" >
    <!-- <button type="cerca"  >clicca</button> -->
   </div>
  </div>
</header>
</template>

<style lang="scss" scoped>
header {
background-color: black;

  h1 {
  color:red;
}
}

</style>
