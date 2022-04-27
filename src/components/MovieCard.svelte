<script>
	// @ts-nocheck
	export /**
	 * @type {{ id: any; }}
	 */
	let movie;
</script>

<div class="movie-card">
	<img alt={movie.title} src={`https://image.tmdb.org/t/p/w500` + movie.poster_path} />
	<div class="descr">
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
</style>
