<template>
  <header>
      <div class="logo">
          <img :src="logoSrc" :alt="logoAlt">
      </div>
  </header>
</template>

<script>
export default {
    name: 'Header',
    props: ['logoSrc', 'logoAlt']
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';
    header {
        padding: 10px;
        background-color: $bgColorLight;
        .logo {
            max-width: 50px;
            img {
                width: 100%;
            }
        }
    }
</style>