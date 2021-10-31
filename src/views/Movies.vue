<template>
    <div class="movies">
        <h2>The spot for movies</h2>
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