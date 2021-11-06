<template>
    <div class="movies">
        <MovieLayout :movies="movies" />
    </div>
</template>

<script>
    import MovieLayout from "@/components/MovieLayout.vue";
    export default {
        name: "Movies",
        components: {
            MovieLayout,
        },
        data() {
            return { }
        },
        computed: {
            movies() {
                return this.$root.$data.movies.docs;
            },
        }
    }
</script>

<style scoped>
    
</style>