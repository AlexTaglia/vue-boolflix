<template>
    <div class="card p-2" >
        <div class="poster">
            <!-- <img :src="`https://image.tmdb.org/t/p/w342${pathImg}`" alt="`Poster of ${title}`"> -->
            <img :src="getPathImg(pathImg)" :alt="`Poster of ${title}`">

        </div>
        <div class="info p-3">
            <div>Title: {{title}} </div>
            <div v-if="title != originalTitle">Original Title: {{originalTitle}} </div>
            <div>
                <span> Language: {{language}} </span> 
                <img class="flag" :src="getFlag(language)" :alt="language">
                <!-- <img class="flag" :src="require(`../assets/flags/${language}.svg`)" :alt="language"> -->
            </div>
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

    },
    methods:{
        getFlag: function(fileName){
            return require(`../assets/flags/${fileName}.svg`)
        },
        getPathImg: function(pathImg){
            return (`https://image.tmdb.org/t/p/w342${pathImg}`)
        }
    }
}
</script>

<style lang="scss" scoped>
  @import '../style/_colors.scss';

    .card{
        
        .poster{
            img {
                width: 100%;
                object-fit: cover;
            }
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

            .flag{
                width: 16px;
            }
        }
    }


</style>