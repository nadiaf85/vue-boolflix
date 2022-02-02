<template>
  <header>
    <h1>Boolflix</h1>

  </header>
</template>

<script>


export default {
  name: 'Header',
  props: {
    msg: String
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
