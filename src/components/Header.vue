<template>
  <header>
      <div class="logo">
          <img :src="logoSrc" :alt="logoAlt">
      </div>
      <select name="" id="" v-model="selectedValue" @change="$emit(`selectGenre`, selectedValue)">
        <option value="">Seleziona genere</option>
        <option value="Rock">Rock</option>
        <option value="Pop">Pop</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
    </select> 
  </header>
</template>

<script>

export default {
    name: 'Header',
    props: ['logoSrc', 'logoAlt'],
    data(){
        return {
            selectedValue: ""
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