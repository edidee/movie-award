<template>
    <div class="container">

        <div class="display-movie"  :key="movies.imdbID">
           <p>Results from search:</p>
            <h3>Title: {{ movies.Title }}</h3>
            <p>Year of Release: {{ movies.Year }}</p>
            <p>Rated: {{ movies.Rated }}</p>

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