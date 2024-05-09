<script>
export default {
  props: {
    moviedObj: Object,
  },
  data() {
    return {
      show: true,
      animation: false,
    };
  },
  methods: {
    // Metodo per ottenere l'icona della bandiera corrispondente alla lingua
    getLanguageFlagIcon(language) {
      if (!language) return "";
      switch (language.toLowerCase()) {
        case "it":
          console.log("Caricata immagine per lingua italiana");
          return new URL(`../assets/img/it.jpg`, import.meta.url).href;
        case "en":
          return new URL(`../assets/img/en.jpg`, import.meta.url).href;
        case "es":
          return new URL(`../assets/img/es.jpg`, import.meta.url).href;
        case "gl":
          return new URL(`../assets/img/gl.jpg`, import.meta.url).href;
        default:
          return new URL(`../assets/img/mondo.jpg`, import.meta.url).href;
      }
    },
    convertVote(vote) {
      return Math.ceil(vote / 2);
    },
    getVision (event) {
      event.preventDefault(); 
      this.show = false;
      setTimeout (( ) => {
        this.animation = false;
      }, 1000);
    },
    getVisionBack (event) {
      event.preventDefault(); 
      this.show = true;
      if(!this.animation) {
        setTimeout (( ) => {
        this.animation = true;
      }, 1000);
      }
    }
  
  },
};
</script>

<template>
  <div class="card" @mouseover="getVision" @mouseleave="getVisionBack">
    <div class="front" v-show="show">
      <div>
        <img
          v-if="moviedObj.poster_path === null && moviedObj.backdrop_path === null"
          class="pellicola"
          src="../assets/img/pellicola.jpg"
          alt=""
        />
        <img class="pellicola"
          v-else
          :src="`https://image.tmdb.org/t/p/w342/${moviedObj.poster_path}`"
          alt=""
        />
      </div>
       
    </div>
    <div class="back" v-show="!show ">
      <h1 v-if="moviedObj.title">Titolo: {{ moviedObj.title }}</h1>
      <h1 v-else>Titolo: {{ moviedObj.name }}</h1>
      <h2 v-if="moviedObj.original_title">Titolo originale: {{ moviedObj.original_title }}</h2>
      <h2 v-else>Titolo originale: {{ moviedObj.original_name }}</h2>
      <img :src="getLanguageFlagIcon(moviedObj.original_language)" class="lang" alt="" />
      <h4>
        <i
          v-for="index in 5"
          :class="{ 'star-filled': index <= Math.ceil(moviedObj.vote_average / 2) }"
          class="fa-solid fa-star"
        ></i>
      </h4>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.card {
  background-color: black;
  color: white;
  max-width: 100%;
   height: 450px;
  perspective: 1000px;
  transition: transform 0.5s;
  position: relative; 

  &:hover {
    transform: rotateY(180deg);
    
    .back {
  
     transform: rotateY(180deg);
   }
  }

  .front .back { 
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
  }

  .back {
    text-align: center;
  
    h1{
      font-size: 1.5rem;
      padding-top:10px;
    }

    h2 {
      font-size: 1rem;
      padding-bottom: 10px;
    }
  }

  .pellicola {
    max-width: 100%;
  height: 450px;
}



.fa-solid {
  color: white;
  border: 1px solid black;
}

.star-filled {
  color: yellow;
}
.lang {
  width: 25%;
  margin: 10px;
}
}





</style>
