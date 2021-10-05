<template>
  <div id="app">
    <Header :logoSrc="require(`./assets/spotify-logo.png`)" :logoAlt="`Spotify Logo`" @selectGenre="filterGenre" @selectAuthor="filterAuthor" :genreList="genreList" :authorList="authorList"/>
    <main>
      <Albums :genre="option" :author="authors" @genreList="genreListEvent" @authorList="authorListEvent"/>
    </main> 
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Albums from './components/Albums.vue';

export default {
  name: 'App',
  components: {
    Header,
    Albums
  },
  data(){
    return {
      option: "",
      authors:"",
      genreList: [],
      authorList: []
    }
  },
  methods: {
    filterGenre(selectedValue){
      this.option = selectedValue;
    },
    filterAuthor(selectedValue){
      this.authors = selectedValue;
    },
    genreListEvent(list){
      this.genreList = list;
    },
    authorListEvent(list){
      this.authorList = list;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common';
</style>
