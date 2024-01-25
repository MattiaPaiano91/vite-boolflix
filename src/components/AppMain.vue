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
               flagUrl = 'jp.png';
            }
            else{
                flagUrl += flag + '.png'
            }
            return flagUrl;
        }
    },
    props:{
        result:Array
    },
}
           
            
</script>

<template>
    <main>
        <div v-for="(elem,i) in result" >
            <ul>
                <li>Title:{{ elem.title }}</li>
                <li>Original title:{{ elem.original_title}}</li>
                <li>
                    <img :src="rightFlag(elem.original_language)" :alt=elem.original_language>
                </li>
                <li>vote:{{ elem.vote_average}}</li>
            </ul>
        </div>
    </main>
</template>

           

<style lang="scss" scoped>
@use "../assets/scss/main.scss" as *;
</style>
