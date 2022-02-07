<template>
    <main>
        <div class="container">
            <div class="row d-flex justify-content-space-around">
                <Catalogo 
                    v-for="(element, index) in filmArray"
                    :key="index"
                    :info="element" />

                <Catalogo 
                    v-for="(serie, indiceSerie) in serieTvArray"
                    :key="indiceSerie+'bc'"
                    :info="serie" />
            </div>
        </div>
    </main>
</template>

<script>

import Catalogo from '../commons/Catalogo.vue';

export default {
    name:'Main',
    components:{
        Catalogo
    },
    props: {
        filmArray: Array,
        serieTvArray: Array,
    },
      
}
</script>

<style lang='scss' scoped>

main{
    min-height: calc(100vh - 56px);
    background-color: #595959 ;
}
</style>
