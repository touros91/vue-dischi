<template>
    <div class="album">
        <div class="image">
            <img :src="card.poster" alt="">
        </div>
        <div class="info">
            <h4 class="title">{{card.title.toUpperCase()}}</h4>
            <h5 class="artist">{{card.author}}</h5>
            <h5 class="year">{{card.year}}</h5>      
        </div>        
    </div>    
</template>

<script>
export default {
    name: 'Album',
    props: ['card']
}
</script>

<style lang="scss" scoped> 
@import '../assets/style/common';

.album {
    width: calc(100% / 5 - 30px);
    margin: 5px 15px;
    background-color: $bgHeader;
    text-align: center;
    color: $mainTextColor;
    padding-bottom: 9px;
    .image{
        max-width: 130px;
        margin: 0 auto;
        padding: 10px;
        img {
            width: 100%;
        }
    }
    .info {
        max-width: 110px;
        text-align: center;
        margin: 0 auto;
        .title {
            color: white;
            font-size: 16px;
            font-weight: 500;
            margin-bottom: 20px;
        }
    }
}
</style>