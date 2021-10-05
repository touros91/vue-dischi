<template>
  <header>
        <div class="logo">
            <img :src="logoSrc" :alt="logoAlt">
        </div>
        <div class="selects">
            <select name="" id="" v-model="selectedValue" @change="$emit(`selectGenre`, selectedValue)">
                <option value="">Seleziona genere</option>
                <option v-for="(genre, index) in genreList" :key="index">{{genre}}</option>
            </select> 
            <select name="" id="" v-model="selectedAuthor" @change="$emit('selectAuthor', selectedAuthor)">
                <option value="">Seleziona autore</option>
                <option v-for="(author, i) in authorList" :key="i">{{author}}</option>
            </select> 
        </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: ['logoSrc', 'logoAlt', 'genreList', 'authorList'],
    data(){
        return {
            albums: [],
            selectedValue: "",
            selectedAuthor: ""
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';
    header {
        height: 50px;
        padding: 10px;
        background-color: $bgHeader;
        display: flex;
        justify-content: space-between;
        .logo {
            max-width: 40px;
            img {
                width: 100%;
            }
        }
        .selects {
            width: 300px;
            display: flex;
            justify-content: space-between;
            align-content: center;
            select {
                margin: 0 10px;
            }
        }
    }
</style>