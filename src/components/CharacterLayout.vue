<template>
    <div class="character_layout">
        <h1>Search for quotes by character!</h1>
        <h2>Popular characters: </h2>
        <router-link class="character_name" v-for="character in characters.filter(character => popular_name.includes(character.name))" :key="character._id" :to="{name: 'Quotes', params: {id: character._id, isMovie: false, name: character.name}}">-{{character.name}}-</router-link>
        <h2>All characters: (many lack dialog)</h2>
        <div class="my_list">
            <router-link class="character_name" v-for="character in characters" :key="character._id" :to="{name: 'Quotes', params: {id: character._id, isMovie: false, name: character.name}}">-{{character.name}}-</router-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CharacterLayout',
    props: {
        characters: Array
    },
    data() {
        return {
            popular_name: ['Samwise Gamgee', 'Bilbo Baggins', 'Gandalf', 'Aragorn II Elessar', 'Gimli', 'Gollum'],
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

    .my_list {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
    }
    .character_name {
        text-decoration: none;
        color:#61996c;
        padding: 5px;
        font-size: x-large;
    }
    
</style>
