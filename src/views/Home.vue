<template>
    <div class="home">
        <div class="logo">
            <img alt="The One Ring" src="../assets/ring.jpg">
        </div>
        <div>
            <h2>Every quote from the Lord of the Rings movies</h2>
        </div>
        <!--<HomeLayout msg="Welcome to The One Website"/>-->
    </div>
</template>

<script>
// @ is an alias to /src
// import HomeLayout from '@/components/HomeLayout.vue'

export default {
    name: 'Home',
    // components: {
    //     HomeLayout
    // }
}
</script>

<style scoped>
    .logo {
        display: flex;
        flex-shrink: 1;
        justify-content: center;
    }
    img {
        width: 100%;
        max-width: 1000px;
    }
</style>
