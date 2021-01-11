<template>
    <div class="container">
       <h1>The Shoppies</h1>
       <div class="input-div">
           <form action="">
               <label for="title">Movie title:</label><br>
               <input type="text" id="title" placeholder="enter movie title" v-model="keyword">
               <button @click.prevent="searchMovie">Search</button>
           </form>
       </div>
       <div class="display-movie" v-for="movie in movies" :key="movie.imdbID">
           <p>Results from search:</p>
            <h3>Title: {{ movie.Title }}</h3>

       </div>
        
    
    </div>
</template>

<script>
export default {
    name: 'DisplayMovies',
    props: { 
        movies: Array,
        searchMovie: Function
    },
    data: () => ({
        keyword: ""
    }),
    // methods: {
    //     searchMovie() {
    //         console.log(`Checking name: ${this.keyword}`);
    //     }
    // }
}
</script>

<style scoped>
    .container{
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

    /* .display-movie{
        display: none;
    } */
</style>