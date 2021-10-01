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
        height: 50px;
        padding: 10px;
        background-color: $bgHeader;
        .logo {
            max-width: 40px;
            img {
                width: 100%;
            }
        }
    }
</style>