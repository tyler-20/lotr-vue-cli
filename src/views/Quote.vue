<template>
    <div class="Quote">
        <h1>Quotes from {{name}}</h1>
        <QuoteLayout :isMovie="getIsMovie" :ID="getID"/>
    </div>
</template>

<script>
    import QuoteLayout from '@/components/QuoteLayout.vue';

    export default {
        name: 'Quote',
        components: {
            QuoteLayout
        },
        computed: {
            getIsMovie() {return Boolean(this.$route.params.isMovie);},
            getID() {return this.$route.params.id;},
            name() {return this.$route.params.name;}
        }
    }
</script>

<style scoped>
    
</style>