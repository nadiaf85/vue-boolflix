<template>
    <main>
        <Searchbar @cerca="filmFiltrati"/>

        <Catalogo 
            v-for="(element, index) in filmArray"
            :key="index"
            :info="element" />
    </main>
</template>

<script>
import axios from 'axios';
import Searchbar from '../commons/Searchbar.vue';
import Catalogo from '../commons/Catalogo.vue';

export default {
    name:'Main',
    components:{
        Searchbar,
        Catalogo
    },
    data(){
        return{
            apiUrl:'https://api.themoviedb.org/3/search/movie',
            filmArray: [],
            inputRicercaFilm: "*",
        }
    },
    created(){
        this.getFilm();
    },
    methods:{
        getFilm(){
            axios.get(this.apiUrl, {
            params: {
                api_key: '5858800bf2416316499f5e0f4a3abde9',
                query: this.inputRicercaFilm,
                language: 'it-IT',
            }
        })
            .then((risposta) => {
                this.filmArray = risposta.data.results
                console.log(this.filmArray);
            })
            .catch(function (error) {
                console.log(error);
            });
        },
        filmFiltrati(inputcerca){
            this.inputRicercaFilm = inputcerca;
            this.getFilm()
        }
    }
}
</script>

<style lang='scss' scoped>

</style>
