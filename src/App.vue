<template>
  <div id="app">
    <Header :logoSrc="require(`./assets/spotify-logo.png`)" :logoAlt="`Spotify Logo`" @selectGenre="filterGenre"/>
    <main>
      <Albums :genre="option"/>
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
    }
  },
  methods: {
    filterGenre(selectedValue){
      this.option = selectedValue;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common';
</style>
