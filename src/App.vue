<template>
  <div id="app">
    <Header :logoSrc="require(`./assets/spotify-logo.png`)" :logoAlt="`Spotify Logo`" @selectGenre="filterGenre" @selectAuthor="filterAuthor"/>
    <main>
      <Albums :genre="option" :author="authors"/>
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
      authors:""
    }
  },
  methods: {
    filterGenre(selectedValue){
      this.option = selectedValue;
    },
    filterAuthor(selectedValue){
      this.authors = selectedValue;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common';
</style>
