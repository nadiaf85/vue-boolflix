<template>
  <header>
    <div>
    <h1>Boolflix</h1>

    <Searchbar @cerca="filmPassati"/>
    </div>
  </header>
</template>

<script>
import Searchbar from '../commons/Searchbar.vue';

export default {
  name: 'Header',
  components:{
        Searchbar,
      },
  props: {
    msg: String
  },
  methods:{
    filmPassati(inputPassati){
      this.$emit('passaFilm', inputPassati)
    }

  }
}
</script>


<style lang="scss" scoped>

header{
  background-color: black;
  height: 50px;

    h1{
    text-transform: uppercase;
    color: red;}

}
</style>
