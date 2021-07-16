<template>
  <header class="d-flex justify-content-between align-items-center">
    
    <div class="logo">
      <img src="../assets/Netflix-logo.png" alt="">
    </div>

    <div class="search-bar">
      <input type="text" placeholder="search" v-model="search">
    </div>
  </header>
</template>

<script>

export default {
  name: 'Header',
  data(){
    return{
      search: '',
    }
  }
}
</script>

<style scoped lang="scss">
  @import '../style/_colors.scss';

  header{
    background-color: $bg-header;
    padding: 10px;
    .logo{
      width: 100px;
      img{
        width: 100%
      }

    }
  }

</style>