<template>
    <div class="container_form">
        <input class="form-control" type="text" placeholder="Cerca film" v-model.trim="inputText">
        <button @click.prevent="$emit('cerca',inputText)">Search</button>
    </div>
</template>

<script>
export default {
    name: 'Searchbar',
    data(){
        return {
            inputText: ""
        }
    }
}
</script>

<style lang='scss' scoped>

</style>