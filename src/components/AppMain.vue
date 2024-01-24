<script>
export default {
    data() {
        return {

        };
    },
    methods: {

    },
    props:{
        result:Array
    }
}
</script>

<template>
    <main>
        <div v-for="(elem,i) in result" >
            <ul>
                <li>Title:{{ elem.title }}</li>
                <li>Original title:{{ elem.original_title}}</li>
                <li>Language:{{ elem.original_language}}</li>
                <li>vote:{{ elem.vote_average}}</li>
            </ul>
        </div>
    </main>
</template>

           

<style lang="scss" scoped>
@use "../assets/scss/main.scss" as *;
</style>
