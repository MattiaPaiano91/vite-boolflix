<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import { data } from './store.js';

export default {
    data() {
        return {
            data
        };
    },
    components: {
        AppHeader,
        AppMain,
        AppFooter
    },  
    methods: {
        startSearchMovie(){
             axios
            .get('https://api.themoviedb.org/3/search/movie', {
                    params: {
                        api_key: 'b2a56f38f368b892b40ea39dbe61874e',
                        query: this.data.userSearch,
                    }
                })
            .then((response) => {
                console.log(response.data.results);
                this.data.movie = response.data.results
            })
        },
         startSearchTv(){
             axios
            .get('https://api.themoviedb.org/3/search/tv', {
                    params: {
                        api_key: 'b2a56f38f368b892b40ea39dbe61874e',
                        query: this.data.userSearch,
                    }
                })
            .then((response) => {
                console.log(response.data.results);
                this.data.tv = response.data.results
            })
        },
    },
    }

</script>
                

<template>
   
    <AppHeader 
        @userSearch="startSearchMovie(), startSearchTv()" 
    />

    <AppMain 
        :resultMovie="this.data.movie"
        :resultTV="this.data.tv" />
    <AppFooter />

</template>

<style lang="scss">
    @use "assets/scss/main" as *;
    @import "assets/scss/partials/reset";
</style>

        
                
            
                   
                

