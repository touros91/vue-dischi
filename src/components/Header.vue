<template>
  <header>
      <div class="logo">
          <img :src="logoSrc" :alt="logoAlt">
      </div>
      <select name="" id="" v-model="selectedValue" @change="$emit(`selectGenre`, selectedValue)">
        <option value="">Seleziona genere</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
    </select> 
  </header>
</template>

<script>
// import Select from './Select.vue';

export default {
    name: 'Header',
    // components: {
    //     Select
    // },
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