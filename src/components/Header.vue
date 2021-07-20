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

    <div class="search-bar d-flex" :class="{'search-bar-none': isActive }">
        <i class="fas fa-search" @click="isActive = !isActive"></i>
      <div class="search-bar-inner d-flex" :class="{'d-none': isActive }" >
        <input type="text" placeholder="Movie, tv series" v-model="searchMedia" @keyup.enter="$emit('search', searchMedia)">
        <button v-if="searchMedia !== ''" class="cross" @click="resetForm"><i class="fas fa-times"></i></button>
        <button @click="$emit('search', searchMedia)">Search</button>
      </div>
    </div>
  </header>
</template>

<script>

export default {
  name: 'Header',
  data(){
    return{
      searchMedia: '',
      isActive: true,
    }
  }, 
  methods:{

    // ToDo
    
    resetForm: function (){
        this.searchMedia='';
        console.log('clear')
    }
    
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
        background-color: $input;
        color: $text-white;
        border: 1px solid $text-white;
        padding: 4px 0;

          i{
            padding: 0 6px;
            line-height: 26px;
          }
        .search-bar-inner{

    
          input{
            background-color: transparent;
            color: $text-white;
            outline: none;
            border:none;
          }      
          
          button{
            border: none;
            padding: 0 4px;
            height: 28px;
            line-height: 26px;
            font-size: 12px;
            background-color: transparent;
            color: $text-white;
          }
        }
        }
    
    .search-bar-none{
      background-color: transparent;
      border: none;
    }
  }

</style>