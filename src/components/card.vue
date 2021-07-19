<template>
    <div class="card p-2" >
        <div class="poster">
            <img :src="`https://image.tmdb.org/t/p/w342${pathImg}`" alt="">
        </div>
        <div class="info p-3">
            <div>Title: {{title}} </div>
            <div v-if="title != originalTitle">Original Title: {{originalTitle}} </div>
            <div>Language: {{language}} </div>
            <div>Vote: {{vote}} </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props:{
        pathImg: String,
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,

    }
}
</script>

<style lang="scss" scoped>
  @import '../style/_colors.scss';

    .card{
        
        img {
            width: 100%;
            object-fit: cover;
        }
        
        .info{
            height: 100%;
            width: 100%;
            position: absolute;
            color: $text-white;
            opacity: 0;
            background-color: rgba(0, 0, 0, 0.5);
            transition: 0.3s;
            font-size: 16px;

            &:hover{
            opacity: 1;            
            }
        }
    }


</style>