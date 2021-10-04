<template>
  <header>
        <div class="logo">
            <img :src="logoSrc" :alt="logoAlt">
        </div>
        <div class="selects">
            <select name="" id="" v-model="selectedValue" @change="$emit(`selectGenre`, selectedValue)">
                <option value="">Seleziona genere</option>
                <option v-for="(album, index) in dynamicGenres" :key="index">{{album}}</option>
            </select> 
            <select name="" id="" v-model="selectedAuthor" @change="$emit('selectAuthor', selectedAuthor)">
                <option value="">Seleziona autore</option>
                <option v-for="(alb, i) in dynamicAuthors" :key="i">{{alb}}</option>
            </select> 
        </div>
  </header>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Header',
    props: ['logoSrc', 'logoAlt'],
    data(){
        return {
            albums: [],
            selectedValue: "",
            selectedAuthor: ""
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((resp) => {
            this.albums = resp.data.response;
        });
    },
    computed: {
        dynamicGenres(){
            var filteredGenres = [];
            this.albums.filter(
                (elm)=> {
            // se non è duplicato ritorna true
                    if (filteredGenres.indexOf(elm.genre) == -1) {
                        filteredGenres.push(elm.genre);
                        return true;
                    }
                    return false;
                }
            );
            return filteredGenres;
        },
        dynamicAuthors(){
            var filteredAuthors = [];
            this.albums.filter(
                (elm)=> {
            // se non è duplicato ritorna true
                    if (filteredAuthors.indexOf(elm.author) == -1) {
                        filteredAuthors.push(elm.author);
                        return true;
                    }
                    return false;
                }
            );
            return filteredAuthors;
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