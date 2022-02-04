<template>
  <div id="app">
    <Header @passaFilm="dataApi"/>
    <Main :filmArray="filmArray" :serieTvArray="serieTvArray"/>
  </div>
</template>

<script>
import Header from './components/macro/Header.vue'
import Main from './components/macro/Main.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
        return{
            inputText: "",
            filmArray: [],
            serieTvArray: [],
        }
  },
  methods:{
    dataApi(inputFiltrati){
        this.inputText = inputFiltrati
        this.getFilm();
        this.getSerieTv();
    },
    getFilm(){
            axios.get('https://api.themoviedb.org/3/search/movie', {
            params: {
                api_key: '5858800bf2416316499f5e0f4a3abde9',
                query: this.inputText,
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
                query: this.inputText,
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

<style lang="scss">
@import "./assets/style/globals.scss";
</style>
