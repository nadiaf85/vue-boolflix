<template>
    <main>
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

</style>
