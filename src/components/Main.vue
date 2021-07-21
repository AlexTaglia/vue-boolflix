<template>
    <main class="container-fluid">
      <div class="row">
        <h1>ORIGINALI NETFLIX</h1>
        <Card class="card col-2 p-0"
        v-for="film in media"
        :key="film.id"
        :pathImg="film.poster_path"
        :title="film.title"
        :titleTv="film.original_name"
        :type="film.media_type"
        :originalTitle="film.original_title"
        :language="film.original_language"
        :vote="film.vote_average"
        
        />
      </div>
    </main>
</template>

<script>
import Card from './card.vue'

export default {
  name: "Main",
  components:{
    Card
  },
  props:{
    media: Array,
  }
};
</script>

<style lang="scss" scoped>
  @import '../style/_colors.scss';

  main {
    height: calc(100vh - 76.25px);
    background-color: $bg-dark;
    overflow-y: auto ;
    overflow-x: hidden ;


    h1{
      color: $text-white;
      font-size: 25px;
    }

    .card{
      border: none;
      border-radius: 6px;
      overflow: hidden;
      background-color: transparent;
    }

  }

</style>