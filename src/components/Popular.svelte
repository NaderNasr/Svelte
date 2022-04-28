<script>
  export /**
* @type {any[]}
*/
   let popularMovies;
  // console.log(popularMovies)
  import MovieCard from "./MovieCard.svelte";

</script>

<h1>Popular Movies</h1>
<div class="popular">
  <!-- Rendering each movie -->
  {#each popularMovies as movie}
    <MovieCard {movie}/>
  {/each}
</div>

<style>
  h1{
    padding: 0 1rem;
  }
  .popular{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-column-gap: 1rem;
    grid-row-gap: 1rem;
  }
</style>