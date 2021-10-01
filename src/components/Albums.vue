<template>
    <section>
        <div class="albums-container">
            <Album v-for="(album, index) in albums" :key="index" :card="album"/>           
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import Album from '../components/Album.vue';

export default {
    name: 'Albums',
    components: {
        Album
    },
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
        position: relative;
        top: 50%;
        transform: translateY(-50%);
        margin: auto;
        display: flex;
        flex-wrap: wrap;
        padding: 10px; 
    }
}
</style>