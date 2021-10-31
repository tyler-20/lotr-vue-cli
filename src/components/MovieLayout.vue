<template>
    <div class="movie_layout">
        <div class="my_list">
            <router-link v-for="movie in movies" :key="movie._id" :to="{name: 'Quotes', params: {id: movie._id, isMovie: true, name: movie.name}}">{{movie.name}}</router-link>
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
h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
.my_list {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    height: 750px;
}
</style>
