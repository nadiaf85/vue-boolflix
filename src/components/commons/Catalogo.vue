<template>
    <ul class="container_info">
        <img :src="'https://image.tmdb.org/t/p/w500/'+info.poster_path" alt="">
        <li v-if="info.title">{{info.title}}</li>
        <li v-else>{{info.name}}</li>
        <li>{{info.original_title}}</li>
        <li><img :src="languageFlag()" alt=""></li>
        <li><i v-for="(element, index) in getStar()" :key="index" class="fas fa-star rating-star"></i></li>
        
    </ul>
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
        getStar(){
            return Math.round(this.info.vote_average / 2)
        }
    }
}
</script>

<style lang="scss" scoped>
    
.container_info{
    width: 100%;
    height: 200px;
    display: flex;
    flex-direction: column;
    justify-content: center;

    img{
        width: 5%;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }
}

    ul li{
        list-style-type: none;
    }


</style>