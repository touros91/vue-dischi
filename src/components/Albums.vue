<template>
    <section>
        <div class="albums-container">
            <Album v-show="filteredAlbumsbyAuthor.length > 1" v-for="(album, index) in filteredAlbums" :key="index" :card="album"/>  
            <Album v-show="filteredAlbumsbyAuthor.length == 1" v-for="(album, index) in filteredAlbumsbyAuthor" :key="index" :card="album"/>          
        </div>
    </section>
</template>

<script>
import axios from 'axios';
import Album from '../components/Album.vue';

export default {
    name: 'Albums',
    props: ['genre', 'author'],
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
            const genreList = [];
            this.albums.forEach(
                (elm) => {
                    if(!genreList.includes(elm.genre)){
                        genreList.push(elm.genre);
                    }
                }
            );
            this.$emit('genreList', genreList);

            const authorList = [];
            this.albums.forEach(
                (elm) => {
                    if(!authorList.includes(elm.author)){
                        authorList.push(elm.author);
                    }
                }
            );
            this.$emit('authorList', authorList);
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
        },
        filteredAlbumsbyAuthor(){
            const authorFiltered = this.albums.filter(
                (elm) => {
                    if (this.author == elm.author || this.author == "") {
                        return true;
                    } 
                    return false;
                }
            );
            return authorFiltered;
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