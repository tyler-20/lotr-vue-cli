<template>
    <div v-if="quotes.length != 0" class="quote_layout">
        <div v-for="quote in quotes" :key="quote._id">
            <h1>{{quote.dialog}}</h1>
        </div>
    </div>
    <div v-else>
        <h2>No Quotes Available</h2>
    </div>
</template>

<script>
    import axios from "axios";

    export default {
        name: 'QuoteLayout',
        props: {
            isMovie: Boolean,
            ID: String,
        },
        data() {
            return {
                quotes: [],
            }
        },
        created: function() {
            let temp_url = 'https://the-one-api.dev/v2';
            temp_url = this.isMovie? temp_url.concat('/movie/'): temp_url.concat('/character/');
            temp_url = temp_url.concat(this.ID + '/quote');
            console.log(temp_url);
            axios.get(temp_url, {
                headers: {
                    authorization: "Bearer 3w1FDe-ShtM-xvbg-o6h" //PUBLIC TOKEN, ACCEPTABLE FOR CLIENT SIDE
                }
            }).then(response => {
                console.log(response);
                this.quotes = response.data.docs;
            }).catch(error => {
                console.log(error);
            })
        },
    }
</script>