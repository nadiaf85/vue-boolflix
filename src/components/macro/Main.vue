<template>
    <main>
        <Searchbar/>
    <div>
        <ul>
            <li></li>
        </ul>
    </div>

    </main>
</template>

<script>
import axios from 'axios';
import Searchbar from '../commons/Searchbar.vue';

export default {
    name:'Main',
    components:{
        Searchbar
    },
    data(){
        return{
            apiUrl:"https://api.themoviedb.org/3/search/movie",
            datiArray: []
        }
    },
    methods:{
        getFilm(){
            axios.get(this.apiUrl, {
            params: {
                apiKey: '5858800bf2416316499f5e0f4a3abde9',
                query: 'anelli'
            }
            })
            .then((risposta) => {
                this.datiArray = risposta.data.results
                console.log(this.datiArray);
            })
            .catch(function (error) {
                console.log(error);
            });
        }
    }
}
</script>

<style lang='scss' scoped>

</style>
