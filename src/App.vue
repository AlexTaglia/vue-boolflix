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
      apiMultiSearch: "https://api.themoviedb.org/3/search/multi?api_key=f865c89fd276891cde3cc08ad6dd6178&query=",
      // apiMovie: "https://api.themoviedb.org/3/search/movie?api_key=f865c89fd276891cde3cc08ad6dd6178&query=",
      // apiTV: "https://api.themoviedb.org/3/search/tv?api_key=f865c89fd276891cde3cc08ad6dd6178&query=",

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

      //Se la mia stringa di ricerca è vuota mi restituisce l'api di default
      if(searchMedia == ""){
        this.apiMultiSearch = this.apiDeafault
      } else{
        // Altrimenti aggiungo la mia ricerca  alla mia stringa dell'api
        this.apiMultiSearch = `https://api.themoviedb.org/3/search/multi?api_key=f865c89fd276891cde3cc08ad6dd6178&query=${searchMedia}`;
        // this.apiMovie = `https://api.themoviedb.org/3/search/movie?api_key=f865c89fd276891cde3cc08ad6dd6178&query=${searchMedia}`;
        // this.apiTV = `https://api.themoviedb.org/3/search/tv?api_key=f865c89fd276891cde3cc08ad6dd6178&query=${searchMedia}`;
      }

      // Genero l'API 
      this.getApi(this.apiMultiSearch)
      // this.getApi(this.apiMovie)
      // this.getApi(this.apiTV)

      console.log(`getString function, input di ricerca: ${searchMedia}`)
     },

    //funzione per lanciare l'API
    getApi: function (api){
      axios.get(api).then((result)=>{
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
