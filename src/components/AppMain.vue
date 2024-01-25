<script>
import { data } from '../store.js';
export default {

    data() {
        return {
           data
        };
    },
    methods: {
      
        rightFlag(flag){
            let flagUrl='https://flagcdn.com/16x12/'
            if(flag == 'en'){
               flagUrl += 'gb-eng.png';
            }else if(flag == 'ja'){
               flagUrl += 'jp.png';
            }
            else{
                flagUrl += flag + '.png'
            }
            return flagUrl;
        }
    },
    props:{
        resultMovie:Array,
        resultTV:Array
    },
}
           
            
</script>

<template>
    <main>
        <div v-for="(elem,i) in resultMovie" >
            <ul>
                <li>Title:{{ elem.title }}</li>
                <li>Original title:{{ elem.original_title}}</li>
                <li>
                    <img :src="rightFlag(elem.original_language)" :alt=elem.original_language>
                </li>
                <li>vote:{{ elem.vote_average}}</li>
                <li><img :src="'https://image.tmdb.org/t/p/w342' + elem.poster_path" :alt="elem.original_title"></li>
            </ul>
        </div>
        <div v-for="(series,j) in resultTV">
            <ul>
                <li>SERIES Title:{{ series.name }}</li>
                <li>Original title:{{ series.original_name}}</li>
                <li>
                    <img :src="rightFlag(series.original_language)" :alt=series.original_language>
                </li>
                <li>vote:{{ series.vote_average}}</li>
                <li><img :src="'https://image.tmdb.org/t/p/w342' + series.poster_path" :alt="series.original_name"></li>
            </ul>
        </div>
    </main>
</template>

<style lang="scss" scoped>
@use "../assets/scss/main.scss" as *;
</style>

           
