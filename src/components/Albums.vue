<template>
    <section>
        <div class="albums-container">
            <div class="album" v-for="(album, index) in albums" :key="index">
                <div class="image">
                    <img :src="album.poster" alt="">
                </div>
                <div class="info">
                    <h4 class="title">{{album.title.toUpperCase()}}</h4>
                    <h5 class="artist">{{album.author}}</h5>
                    <h5 class="year">{{album.year}}</h5>      
                </div>        
            </div>        
        </div>
    </section>
</template>

<script>
import axios from 'axios';

export default {
    name: 'Albums',
    data(){
        return {
            albums: []
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((resp) => {
            this.albums = resp.data.response;
            console.log(this.albums);
        })
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/style/common';
    section {
        height: calc(100vh - 50px);
        background-color: $bgBody;
        .albums-container{
            width: 70%;
            height: calc(100vh - 50px);
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            padding: 15px 0; 
            .album {
                width: calc(100% / 5 - 30px);
                margin: 5px 15px;
                background-color: $bgHeader;
                text-align: center;
                color: $mainTextColor;
                .image{
                    width: 130px;
                    margin: 0 auto;
                    padding: 10px;
                    img {
                        width: 100%;
                    }
                }
                .info {
                    width: 110px;
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
        }
    }

</style>