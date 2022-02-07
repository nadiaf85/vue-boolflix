<template>
    <div class="col-3 d-flex container_card">
        <div class="card">
            <div class="cover">
                <img :src="getImage(info.poster_path)" alt="">
            </div>
            <div class="info">
                <ul>
                    <li v-if="info.title"><strong>Titolo: </strong>{{info.title}}</li>
                    <li v-else>{{info.name}}</li>
                    <li><strong>Titolo originale: </strong>{{info.original_title}}</li>
                    <li><img :src="languageFlag()" alt=""></li>
                    <li><strong>Voto: </strong>
                        <span><i v-for="(element,index) in getStar(info.vote_average)" :key="index" class="fas fa-star rating-star"></i></span>
                        <span><i v-for="(element,index) in (5-getStar(info.vote_average))" :key="index+'j'" class="far fa-star rating-star"></i></span>
                    </li>
                    <li><strong>Overview: </strong>{{info.overview}}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Catalogo',
    props: {
        'info': Object
    },
    methods:{
        languageFlag(){
            if(this.info.original_language == 'it'){
                return require("../../assets/img/ita-flag.jpg")
            }else if(this.info.original_language == 'en'){
                return require("../../assets/img/en-flag.jpeg")
            }else if(this.info.original_language == 'es'){
                return require("../../assets/img/es-flag.jpg")
            }else{
                return require("../../assets/img/bandiera-no.jpeg")
            }
        },
        getImage(){
            if(this.info.poster_path==null){
                return require('../../assets/img/no-image.jpeg')
            }else{
                return 'https://image.tmdb.org/t/p/w342/'+ this.info.poster_path
            }
        },
        getStar(){
            return Math.ceil(this.info.vote_average / 2)
        }
    }
}
</script>

<style lang="scss" scoped>
    
.container_card{
    width: 30%;
    height: 576px;
    padding: 15px;
    margin-right: 20px;
    margin-left: 20px;
    margin-bottom: 20px;
    margin-top: 20px;
    background-color: darkgrey;

    &:hover .info{
      display: block;
      background-color: black;
      }

    .card{
    height: 100%;

    .cover{
        height: 100%;
        position: relative;

        img{
            height: 100%;
            border: 3px solid white;
            object-fit: cover;
            }
        }
    }
}

.info{
    display: none;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    padding: 25px;

    ul li{
        list-style-type: none;
        color: white;
        font-size: 14px;
        font-weight: 400;
    }

    img{
        width: 7%;
    }

    .rating-star{
        color: yellow;
    }

}
</style>