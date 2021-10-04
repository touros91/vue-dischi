<template>
    <select name="" id="" v-model="selectedValue" @change="$emit(`selectGenre`, selectedValue)">
        <option value="">Seleziona genere</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
    </select> 
</template>

<script>
export default {
    name: 'Select',
    data(){
        return {
            selectedValue: ""
        }
    }
}
</script>

<style>

</style>