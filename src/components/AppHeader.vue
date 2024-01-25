<script>
import { data } from '../store.js';
import axios from 'axios';
export default {
    data() {
        return {
            data
        };
    },
    // methods: {
    //        searchFlag(){
    //              axios
    //          .get("https://flagsapi.com/EN/flat/64.png", {
    //              })
    //          .then((response) => {
    //              console.log('flag'+ response);
    //          })
    //      }
    // }
}
</script>
                  

<template>
    <header>
        <form 
        @submit.prevent="$emit('userSearch')"
       
        action="">
            <input v-model="data.userSearch" type="text">
            <button>Cerca</button>
        </form>
    </header>
</template>

<style lang="scss" scoped>
    @use "../assets/scss/main.scss" as *;
</style>

