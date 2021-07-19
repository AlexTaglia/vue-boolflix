<template>
    <div class="card" >

        <div class="poster m-1">
            <!-- <img :src="`https://image.tmdb.org/t/p/w342${pathImg}`" alt="`Poster of ${title}`"> -->
            <img v-if="pathImg !== null"  :src="getPathImg(pathImg)" :alt="`Poster of ${title}`">
            <img class="no-img" v-else src="../assets/no_image.jpg" alt="">

        </div>
        <div class="info p-3">
            <div class="title" v-if="type === 'tv'">{{titleTv}} </div>
            <div class="title" v-if="type === 'movie' || title !== ''">{{title}} </div>
            <div class="title" v-if="title != originalTitle">Original Title: {{originalTitle}} </div>
            <div>
                <span> Language: {{language}} </span> 
                <img class="flag" :src="getFlag(language)" :alt="language">
                <!-- <img class="flag" :src="require(`../assets/flags/${language}.svg`)" :alt="language"> -->
            </div>

            <div>
                <span v-for="(star, index) in yellowStars" :key='index'>
                    <i class="yellowStar fas fa-star" ></i>
                </span> 
                   
                <!-- <span v-for="(star, index) in (5- yellowStars)" :key="'n'+index"> -->
                <span v-for="(star, index) in getEmptyStar(yellowStars)" :key="'n'+index">
                    <i class=" far fa-star" ></i>
                </span>  

                            
            </div>               

        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',

    data: function () {
        return {
            yellowStars: Math.ceil(this.vote / 2),
        }
    },
    
    props:{
        pathImg: String,
        title: String,
        originalTitle: String,
        language: String,
        titleTv: String,
        type: String,
        vote: Number,

    },
    methods:{
        getFlag: function(fileName){
            return require(`../assets/flags/${fileName}.svg`)
        },
        getPathImg: function(pathImg){
            return (`https://image.tmdb.org/t/p/w342${pathImg}`)
        },
        getEmptyStar : function (yellowStars){
            return 5 - yellowStars;
        },
        // getStar : function (vote){
        //     return Math.round(vote / 2)
        // }
  },    
}
</script>

<style lang="scss" scoped>
  @import '../style/_colors.scss';

    .card{
        text-align: center;
        padding: 10px;
        
        .poster{
            img {
                width: 100%;
                object-fit: cover;
                border-radius: 5px;
            }

            .no-img {
                opacity: 0.1;
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

            .title{
                font-size: 22px;
                font-weight: bold;
            }

            .flag{
                width: 16px;
            }

            .yellowStar{
                color: yellow;
            }
        }
    }


</style>