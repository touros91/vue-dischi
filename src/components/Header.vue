<template>
  <header>
      <div class="logo">
          <img :src="logoSrc" :alt="logoAlt">
      </div>
      <select name="" id="" v-model="selectedValue" @change="$emit(`selectGenre`, selectedValue)">
        <option v-for="(album, index) in albums" :key="index">{{album.genre}}</option>
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