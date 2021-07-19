<template>
  <header class="d-flex justify-content-between align-items-center">
    
    <div class="logo">
      <img src="../assets/Netflix-logo.png" alt="">
    </div>

    <div class="search-bar">
      <input type="text" placeholder="search" v-model="searchMedia" @keyup.enter="$emit('search', searchMedia)">
      <button @click="$emit('search', searchMedia)">Search</button>
      <!-- <button @click="resetForm">Reset</button> -->
    </div>
  </header>
</template>

<script>

export default {
  name: 'Header',
  data(){
    return{
      searchMedia: '',
    }
  }, 
  methods:{

    // ToDo
    /*
    resetForm: function (){
        this.searchMedia='';
        console.log('clear')
    }
    */
  }

}
</script>

<style scoped lang="scss">
  @import '../style/_colors.scss';

  header{
    background-color: $bg-dark;
    padding: 10px;

    .logo{
      width: 100px;
      img{
        width: 100%
      }
    }

    .search-bar{
      button{
        border: none;
        margin-left: 15px;
        height: 28px;
      }
    }
  }

</style>