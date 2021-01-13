<template>
    <div class="container">

        <div class="display-movie" v-for="movies in filterWord" :key="movies.imdbID" :style="{ display: displayVar}">
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
        
    },
    data: () => ({
        keyword: "",
        displayVar: 'block'
    }),

    computed: {
        filterWord() {
            return this.movies.filter(movies => {
                return movies.Title.toLowerCase().includes(this.keyword.toLowerCase())
            })
        }
    }
    // methods: {
    //     searchMovie() {
    //         console.log(`Checking name: ${this.keyword}`);
    //     }
    // }
}
</script>

<style scoped>
    
    
</style>