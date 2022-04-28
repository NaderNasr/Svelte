<script>
	// @ts-nocheck
	export /**
	 * @type {{ id: any; }}
	 */
	let movie;
</script>

<div class="movie-card">
	<img alt={movie.title} src={`https://image.tmdb.org/t/p/w500` + movie.poster_path} />
	<div class="desc">
		<h2>{movie.title}</h2>
		<p>{movie.release_date}</p>
	</div>
</div>

<style>
	img {
		width: 100%;
    height: 50vh;
    object-fit: cover;
    border-radius: 1rem;
    margin-bottom: 1rem;
	}
  h2 {
    font-size: 20px;
  }
  desc {
    height: 5vh;
  }
  p {
    font-size: 0.7rem;
  }
  .movie-card{
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    padding: 0.1rem;
  }

</style>
