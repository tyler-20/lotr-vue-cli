<template>
  <div id="app">
    <div id="nav">
      <img id="ring" alt="The One Ring" src="./assets/ring.jpg">
      <div class="links">
        <router-link to="/">Home</router-link>
        <router-link to="/movies">Movies</router-link>
        <router-link to="/characters">Characters</router-link>
      </div>
    </div>
    <router-view/>
    <div class="footer">
      <a href="https://github.com/tyler-20/lotr-vue-cli">GitHub Link</a>
    </div>
  </div>
</template>

<script>
  import axios from "axios";
  export default {
    name: 'app',
    created: function() {
        let url1 = "https://the-one-api.dev/v2/movie";
        let url2 = "https://the-one-api.dev/v2/character";
        let backup_url = "http://localhost:8080";
        axios.get(url1, {
          headers: {
            authorization: "Bearer 3w1FDe-ShtM-xvbg-o6h" //PUBLIC TOKEN, ACCEPTABLE FOR CLIENT SIDE
          }
        })
          .then(response => {
            this.$root.$data.movies = response.data;
          }).catch(error => {
            console.log(error, "importing from backup_movies")
            axios.get(backup_url + '/backup_movies.txt')
            .then(response => {
              console.log(response.data)
              this.$root.$data.movies = response.data;
            })
          });
        axios.get(url2, {
          headers: {
            authorization: "Bearer 3w1FDe-ShtM-xvbg-o6h"
          }
        }).then(response => {
          this.$root.$data.characters = response.data;
        }).catch(error => {
          console.log(error, "importing from backup_characters")
            axios.get(backup_url + '/backup_characters.txt')
            .then(response => {
              console.log(response.data)
              this.$root.$data.characters = response.data;
            })
        })
      }
  }
</script>

<style>
* {
  box-sizing: border-box;
  background-color: #E0E1DD;
}
#app {
  color: #2c3e50;
}
#nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 30px;
  background-color: #ac792c;
  margin-bottom: 20px;
  width: 100%;
}
#nav a {
  font-weight: bold;
  color: #232020;
  font-size: x-large;
  padding: 30px 50px;
  margin: 20px;
}
#nav a.router-link-exact-active {
  color: #61996c;
}
.links {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
  width: 85%;
  background-color: inherit;
  align-items: center;
}
#ring {
  display: flex;
  width: 15%;
  max-width: 350px;
}
.footer {

  margin-top: 250px;
  border-top: #ac792c;
  border-top-style: solid;
  margin-left: 50px;
  margin-right: 50px;
  text-align: right;
  padding: 10px;
  padding-right: 25px;
  font-size: large;
}
</style>