<template>
  <div id="app">
    <Header 
    @search="getString"
    />

    <Main 
    :media="media"
    />

  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },

  data: function() {
    return{
      media: [],
      //API caricata al primo loading
      apiDeafault: "https://api.themoviedb.org/3/movie/popular?api_key=f865c89fd276891cde3cc08ad6dd6178",
      
      //Stringa senza query
      apiMovie: "https://api.themoviedb.org/3/search/movie?api_key=f865c89fd276891cde3cc08ad6dd6178&query=",
    }
  },
  
  created (){
    //First loading con l'API di default
    this.getApi(this.apiDeafault);
  },
  
  methods:{
    // Creo una funzione che unisce la stringa dell'API 
    // con il mio input di ricerca
    getString: function(searchMedia) {
      // aggiungo la mia ricerca  alla mia stringa dell'api
      this.apiMovie += searchMedia 

      // Genero l'API 
      this.getApi(this.apiMovie)

      //Resetto la mia API
      this.apiMovie = "https://api.themoviedb.org/3/search/movie?api_key=f865c89fd276891cde3cc08ad6dd6178&query=";
      console.log(`getString function, input di ricerca: ${searchMedia}`)
      console.log(`apiMovie reset: ${this.apiMovie}`)
     },

    //funzione per lanciare l'API
    getApi: function (api){
      axios.get(api).then((result)=>{
        // this.media = [];
        this.media = result.data.results;
        console.log(`getApi function`)
        
      })
    },
  }  
}
</script>

<style lang="scss">
  @import "./style/app.scss";
  
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
  }
</style>  
