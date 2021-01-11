<template>
  <div id="app">
    
    <DisplayMovies v-bind:movies='movies' />
  </div>
</template>

<script>
import DisplayMovies from './components/DisplayMovies'

export default {
  name: 'App',
  components: {
    DisplayMovies
  },
  data () {
    return {
      movies: []
    }
  },
   methods: {
     searchMovie(){
       this.$http.get(' http://www.omdbapi.com/?i=tt3896198&apikey=42a545b2')
         .then(response => (this.movies = response.data))
         .catch(error => console.log(error))
          .finally(() => this.loading = false)
     }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
