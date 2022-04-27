
<script>
  // @ts-nocheck
  export /**
* @type {{ id: any; }}
*/
   let movie;
</script>


<div class="movie-card">
  <img alt={movie.title} src={`https://image.tmdb.org/t/p/w500` + movie.poster_path}/>
</div>
<div class="descr">
  <h2>{movie.title}</h2>
  <p>{movie.release_date}</p>
</div>


<style></style>