<template>
    <div class="card" v-if="type !== 'person'" >

        <div class="poster m-1" >
            <img v-if="pathImg !== null && pathImg !== undefined"  :src="getPathImg(pathImg)" :alt="`Poster of ${title}`">
            <img class="no-img" v-else src="../assets/no_image.jpg" alt="Poster not found">
        </div>
        
        <div class="info p-3">
            <div class="title" v-if="type === 'movie' || type === undefined">{{title}} </div>
            <div class="title" v-else>{{titleTv}} </div>

            <div>
                <span> Language: {{language}} </span> 
                <img class="flag" :src="getFlag(language)" :alt="language">
            </div>

            <div>
                <i v-for="x in 5" :key="x" class="fa-star" :class="x <= getAverage(vote) ? 'fas yellowStar': 'far' "></i>
            </div>  

            <div class="type">
            {{type}}    
            </div>             

        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
   
    props:{
        pathImg: String,
        title: String,
        titleTv: String,
        originalTitle: String,
        language: String,
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
        getAverage(vote){
            return Math.ceil(vote / 2)
        }
  },    
}
</script>

<style lang="scss" scoped>
  @import '../style/_colors.scss';

    .card{
        text-align: center;
        padding: 10px;
        transition: transform .3s; 

        &:hover{
            transform: scale(1.1);
            z-index: 2;
        }
        
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

            .type{
                position: absolute;
                bottom: 10px;
                left: 10px;
                background-color: red;
                padding: 0 6px;
                border-radius: 4px;
            }
        }
    }


</style>