<script>
import { data } from '../store.js';
import axios from 'axios';
export default {
    data() {
        return {
            data
        };
    },
    methods: {
         
    }
}
</script>
                  

<template>
    <header>
        <form 
        @submit.prevent="$emit('userSearch')"
        action="">
            <div class="input-group mb-3">
                <input v-model="data.userSearch" type="text" class="form-control" placeholder="Recipient's username" aria-label="Recipient's username" aria-describedby="button-addon2">
                <button class="btn btn-outline-secondary" type="submit" id="button-addon2">Cerca</button>
            </div>
        </form>
    </header>
</template>
<!-- <form 
        @submit.prevent="$emit('userSearch')"
        action="">
            <input v-model="data.userSearch" type="text">
            <button>Cerca</button>
        </form> -->
<style lang="scss" scoped>
    @use "../assets/scss/main.scss" as *;
    form{
        width: 1200px;
        margin: 0 auto;
    }
</style>
       

