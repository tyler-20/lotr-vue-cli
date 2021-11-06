<template>
    <div class="character_view">
        <CharacterLayout :characters="characters" />
    </div>
</template>

<script>
    import CharacterLayout from "@/components/CharacterLayout.vue";
    export default {
        name: "Characters",
        components: {
            CharacterLayout,
        },
        data() {
            return {        }
        },
        computed: {
            characters() {
                return this.$root.$data.characters.docs;
            },
        }
    }
</script>