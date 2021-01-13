<template>
  <div id="app">
     <h1>The Shoppies</h1>
       <div class="input-div">
           <form action="">
               <label for="title">Movie title:</label><br>
               <input type="text" id="title" placeholder="enter movie title" v-model="keyword">
               <button @click.prevent="searchMovie">Search</button>
           </form>
       </div>
       
    
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
  data: () => ({
      keyword: "",
      movies: {},
      displayVar: 'block'
    
  }),
   methods: {
     searchMovie() {
       this.$http.get(' http://www.omdbapi.com/?i=tt3896198&apikey=42a545b2',
       {
         params: {
           search: this.keyword
         }
       })
         .then(response => {
           if (this.keyword === ''){
             return;
           }
           this.movies = response.data;
           this.keyword = ''
         } )
         .catch(error => console.log(error))
          .finally(() => this.loading = false)
     },

     displayResult() {
        this.displayVar = 'block'
     }
  },
  // watch: {
  //   keyword(newKeyword, oldKeyword) {
  //     console.log(`New keyword is ${newKeyword}`);
  //     console.log(`Old keyword is ${oldKeyword}`);
  //     this.checkName();
  //   }
  // }
}
</script>

<style>
#app {
      font-family: Avenir, Helvetica, Arial, sans-serif;
        width: 80%;
        height: auto;
        background-color: #eee;
        margin: 0 auto;
}
 

.input-div{
        width: 70%;
        background-color: #fff;
        margin: 0 auto;
    }
</style>
