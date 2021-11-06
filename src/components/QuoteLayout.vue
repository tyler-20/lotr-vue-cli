<template>
    <div v-if="quotes.length != 0" class="quote_layout">
        <div v-for="quote in quotes" :key="quote._id">
            <div class="check_box">
                <input type="checkbox" v-model="quote.checked" @change.prevent="modifyFavorite(quote)"> {{quote.dialog}}
            </div>
        </div>
    </div>
    <div v-else-if="waiting">
        <h2>Loading...</h2>
    </div>
    <div v-else>
        <h2>Sorry, there are no quotes available</h2>
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
                waiting: true,
            }
        },
        methods: {
            modifyFavorite(quote) {
                if (quote.checked == false) {
                    this.$root.$data.saved = this.$root.$data.saved.filter(item => item._id != quote._id);
                } else {
                    this.$root.$data.saved.push(quote);
                }
                return
            },
        },
        created: function() {
            let temp_url = 'https://the-one-api.dev/v2';
            temp_url = this.isMovie? temp_url.concat('/movie/'): temp_url.concat('/character/');
            temp_url = temp_url.concat(this.ID + '/quote');
            this.waiting = true;
            axios.get(temp_url, {
                headers: {
                    authorization: "Bearer 3w1FDe-ShtM-xvbg-o6h" //PUBLIC TOKEN, ACCEPTABLE FOR CLIENT SIDE
                }
            }).then(response => {
                this.quotes = response.data.docs;
                let current_ids = this.$root.$data.saved.map(quote => quote._id)
                for (let i = 0; i < this.quotes.length; i++) {
                    if (current_ids.includes(this.quotes[i]._id) != 0) {
                        this.quotes[i]["checked"] = true;
                    } else {
                        this.quotes[i]["checked"] = false;
                    }
                }
            }).catch(error => {
                console.log(error);
            }).finally(() => {
                this.waiting = false;
            })
        },
    }
</script>

<style scoped>
    h1 {
        font-size: x-large;
        font-weight: normal;
    }
    .check_box {
        font-size: xx-large;
    }
</style>