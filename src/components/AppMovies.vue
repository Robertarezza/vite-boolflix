<script>
export default {
  props: {
    moviedObj: Object,
  },
  data() {
    return {
     
    };
  },
  computed: {
    cardTitle() {
      return !!this.moviedObj.title ? this.moviedObj.title : this.moviedObj.name;
    },
    cardOriginalTitle() {
      return !!this.moviedObj.original_title ? this.moviedObj.original_title : this.moviedObj.original_name ;
    }
  },
  methods: {
    // ottenere l'icona della bandiera corrispondente alla lingua
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
  },
};
</script>

<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="front" >
        <img
          v-if="moviedObj.poster_path === null && moviedObj.backdrop_path === null"
          class="pellicola"
          src="../assets/img/pellicola.jpg"
          alt=""
        />
        <img
          class="pellicola"
          v-else
          :src="`https://image.tmdb.org/t/p/w342/${moviedObj.poster_path}`"
          alt=""
        />
      </div>
      <div class="back" >
        <h1>Titolo: {{ cardTitle }}</h1>
        <h2 >Titolo originale: {{ cardOriginalTitle}}</h2>
        <h3>
        Language: 
          <img
          :src="getLanguageFlagIcon(moviedObj.original_language)"
          class="lang"
          alt=""/>
        </h3>
       
        <h4>
          Voto:
          <i
            v-for="index in 5"
            :class="{ 'star-filled': index <= Math.ceil(moviedObj.vote_average / 2) }"
            class="fa-solid fa-star"
          ></i>
        </h4>
        <p v-if="moviedObj.overview">Overview: {{ moviedObj.overview }}</p>
        <p v-else></p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>

.flip-card {
  background-color: transparent;
  color: white;
  max-width: 96%;
  height: 450px;
  cursor: pointer;
  border-radius: 20px;
  perspective: 1000px;


  .flip-card-inner {
    position: relative;
    width: 100%;
    height: 100%;
    text-align: center;
    transition: transform 0.8s;
    transform-style: preserve-3d;

    &:hover {
      transform: rotateY(180deg);
    }
  }
    
  
  
  .front {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    -webkit-backface-visibility: hidden; /* Safari */
    backface-visibility: hidden;
  }

  .back {
    text-align: center;
    background-color: black;
    transform: rotateY(180deg);
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    -webkit-backface-visibility: hidden; /* Safari */
    backface-visibility: hidden;

    h1 {
      font-size: 1.5rem;
      padding-top: 10px;
    }

    h2 {
      font-size: 1rem;
      padding-bottom: 10px;
    }
    p {
      font-size: x-small;
    }
  }

  .pellicola {
    max-width: 100%;
    height: 450px;
    border-radius: 20px;
  }

  .fa-solid {
    color: white;
    border: 1px solid black;
  }

  .star-filled {
    color: yellow;
  }
  .lang {
    width: 15%;
    margin: 10px;
  }
}

</style>
