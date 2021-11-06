<template>
    <div class="movie_layout">
        <h2>Search for quotes by movie!</h2>
        <div class="my_list">
            <router-link class="movie_name" v-for="movie in movies.filter(movie => (movie.name === 'The Two Towers ' || movie.name === 'The Fellowship of the Ring' || movie.name == 'The Return of the King'))" :key="movie._id" :to="{name: 'Quotes', params: {id: movie._id, isMovie: true, name: movie.name}}">{{movie.name}}</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MovieLayout',
    props: {
        movies: Array
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .movie_name {
        color: #61996c;
        font-size: x-large;
        margin-top: 5px;
        margin-bottom: 5px;
    }
    .movie_name:any-link {
        color: #61996c;
        text-decoration: none;
    }
    .my_list {
        display: flex;
        flex-direction: column;
    }
    h2 {
        font-size: xx-large;
    }
</style>
