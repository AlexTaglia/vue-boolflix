<template>
  <div id="app">
    <Header />
    <Main :media="media"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'
// import testJson from './jsons/testJson.json'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },

  data: function() {
    return{
      // media: testJson,
      media: [],
    }
  },
  
  created (){
    axios.get("https://api.themoviedb.org/3/search/movie?api_key=f865c89fd276891cde3cc08ad6dd6178&query=ritorno+al+futuro").then((result) =>{
      this.media = result.data.results;
      console.log(this.media)
    })
  },
  
}
</script>

<style lang="scss">
  @import "./style/app.scss";
  
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
  }
</style>  
