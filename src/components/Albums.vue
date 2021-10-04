<template>
    <section>
        <div class="albums-container">
            <Album v-for="(album, index) in filteredAlbums" :key="index" :card="album"/>        
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import Album from '../components/Album.vue';

export default {
    name: 'Albums',
    props: ['genre'],
    components: {
        Album
    },
    data(){
        return {
            albums: [],
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((resp) => {
            this.albums = resp.data.response;
        });
    },
    computed: {
        filteredAlbums(){
            const albumsFiltered = this.albums.filter(
                (elm) => {
                    if (this.genre == elm.genre || this.genre == "") {
                        return true;
                    } 
                    return false;
                }
            );
            return albumsFiltered;
        }
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