<template>
  <header>
    <div class="container">
      <div class="row d-flex ">
        <div class="col d-flex justify-content-between align-items-center">
          <h1>Boolflix</h1>
          <div class="search"><Searchbar @cerca="filmPassati"/></div>
        </div>
      </div>
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
  methods:{
    filmPassati(inputPassati){
      this.$emit('passaFilm', inputPassati)
    }

  }
}
</script>


<style lang="scss" scoped>
@import '../../assets/style/globals.scss';

header{
    width: 100%;
    height: 70px;
    display: flex;
    align-items: center;
    background-color: black; 
      
      h1{
        color: red;
        text-transform: uppercase;
        }
}


</style>
