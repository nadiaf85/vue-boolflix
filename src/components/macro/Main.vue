<template>
    <main>
        <Searchbar @cerca="sceltaFilm"/>

        <Catalogo 
            v-for="(element, index) in rispostaApi"
            :key="index"
            :film="element" />
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
            rispostaApi: [],
            inputRicercaFilm: ""
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
            }
        })
            .then((risposta) => {
                this.rispostaApi = risposta.data.results
                console.log(this.rispostaApi);
            })
            .catch(function (error) {
                console.log(error);
            });
        },
        sceltaFilm(inputcerca){
            this.inputRicercaFilm = inputcerca;
            this.getFilm()
        }
    }
}
</script>

<style lang='scss' scoped>

</style>
