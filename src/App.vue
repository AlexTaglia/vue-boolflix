<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import test from './jsons/test.json'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  Data(){
    return{
      testJson: test
    }
  }
}
</script>

<style lang="scss">
  @import "./style/app.scss";
  
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
  }
</style>  
