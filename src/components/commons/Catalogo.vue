<template>
    <ul class="container_info">
        <li v-if="info.title">{{info.title}}</li>
        <li v-else>{{info.name}}</li>
        <li>{{info.original_title}}</li>
        <li><img :src="languageFlag()" alt=""></li>
        <li>{{info.vote_average}}</li>
        
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
                return require("../../assets/img/ita-flag.jpeg")
            }else if(this.info.original_language == 'en'){
                return require("../../assets/img/en-flag.jpeg")
            }else if(this.info.original_language == 'es'){
                return require("../../assets/img/es-flag.jpg")
            }else{
                return require("../../assets/img/bandiera-no.jpeg")
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    
.container_info{
    width: 100%;
    height: 150px;
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