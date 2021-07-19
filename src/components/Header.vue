<template>
  <header class="d-flex justify-content-between align-items-center">
    
    <div class="logo-section d-flex align-items-center">
      <div class="logo">
        <img src="../assets/Netflix-logo.png" alt="">
      </div>
      <div class="menu">
        <ul>
          <li><a href=""></a>Home</li>
          <li><a href=""></a>Serie TV</li>
          <li><a href=""></a>Film</li>
          <li><a href=""></a>Nuovi e popolari</li>
          <li><a href=""></a>La mia lista</li>
        </ul>
      </div>
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

    .menu{
      font-size: 14px;
      padding-top: 10px;
      
      li{
        transition: 0.3s;
      }


      li:hover{
        color: gray;
      }

    }

    .search-bar{
      
      button{
        border: none;
        margin-left: 15px;
        height: 28px;
        line-height: 28px;
        font-size: 12px;
      }
    }
  }

</style>