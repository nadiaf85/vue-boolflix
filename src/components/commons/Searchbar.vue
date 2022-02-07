<template>
    <div class="search d-flex">
        <input class="form-control" type="text" placeholder="Search..." v-model.trim="inputText">
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

input{
    height: 35px;
    border-radius: 6px;
}

button{
    padding: 5px 15px;
    margin-left: 7px;
    border-radius: 6px;
}

</style>