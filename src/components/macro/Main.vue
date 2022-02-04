<template>
    <main>
        <Searchbar @cerca="filmFiltrati"/>

        <Catalogo 
            v-for="(element, index) in filmArray"
            :key="index"
            :info="element" />

        <Catalogo 
            v-for="(serie, indiceSerie) in serieTvArray"
            :key="indiceSerie+'bc'"
            :info="serie" />
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
            filmArray: [],
            serieTvArray: [],
            inputRicercaFilm: "*",
        }
    },
    created(){
        this.getFilm();
        this.getSerieTv();
    },
    methods:{
        getFilm(){
            axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: '5858800bf2416316499f5e0f4a3abde9',
                query: this.inputRicercaFilm,
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
            this.getSerieTv()
        },
        getSerieTv(){
            axios.get('https://api.themoviedb.org/3/search/tv', {
            params: {
                api_key: '5858800bf2416316499f5e0f4a3abde9',
                query: this.inputRicercaFilm,
                language: 'it-IT',
            }
        })
            .then((risposta) => {
                this.serieTvArray = risposta.data.results
                console.log(this.serieTvArray);
            })
            .catch(function (error) {
                console.log(error);
            });
        },
    }
}
</script>

<style lang='scss' scoped>

</style>
