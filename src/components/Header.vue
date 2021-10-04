<template>
  <header>
      <div class="logo">
          <img :src="logoSrc" :alt="logoAlt">
      </div>
      <select name="" id="" v-model="selectedValue" @change="$emit(`selectGenre`, selectedValue)">
          <option value="">Seleziona genere</option>
        <option v-for="(album, index) in dynamicGenres" :key="index">{{album}}</option>
    </select> 
  </header>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Header',
    props: ['logoSrc', 'logoAlt'],
    data(){
        return {
            selectedValue: "",
            albums: []
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
    }
</style>