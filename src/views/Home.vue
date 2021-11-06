<template>
    <div class="home">
        
        <div>
            <h1>All quotes from 'The Lord of the Rings' movies!</h1>
            <h3 v-if="saved.length === 0">View by 'Movie' or 'Character', your favorites will show up here!</h3>
            <div v-else class="items" v-for="quote in saved" :key="quote._id">
                <button @click.prevent="removeFromFavorites(quote)">X</button>
                <h3>{{quote.dialog}}</h3>
                <p>-{{get_name(quote.character)}}, {{get_movie(quote.movie)}}</p>
            </div>
        </div>
        <!--<HomeLayout msg="Welcome to The One Website"/>-->
    </div>
</template>

<script>
// @ is an alias to /src
// import HomeLayout from '@/components/HomeLayout.vue'

export default {
    name: 'Home',
    data() {
        return {
            
        }
    },
    computed: {
        saved() {
            return this.$root.$data.saved;
        },
        
    },
    methods: {
        removeFromFavorites(badQuote) {
            this.$root.$data.saved = this.$root.$data.saved.filter(goodQuotes => goodQuotes != badQuote)
        },
        get_movie(movie_id) {
            return this.$root.$data.movies.docs.filter(movie => movie._id === movie_id)[0].name;
        },
        get_name(character_id) {
            return this.$root.$data.characters.docs.filter(character => character._id === character_id)[0].name;
        }
    },
    // components: {
    //     HomeLayout
    // }
}
</script>

<style scoped>
    * {
        box-sizing: border-box;
        
    }
    button {
        background-color: #ac792c;
        height: fit-content;
        margin-right: 10px;
    }
    .items {
        display: flex;
        flex-direction: row;
        align-items: center;
    }
    h3 {
        font-size: x-large;
        font-weight: normal;
    }
    p {
        margin-left: 15px;
        font-size: x-large;
        font-style: italic;
    }
 
</style>
