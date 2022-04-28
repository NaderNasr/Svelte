<script context="module">
	//fetch api request
	// @ts-ignore
	export async function load({ params }) {
		console.log('params>>', params.id);
		const response = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=${
				import.meta.env.VITE_API_KEY
			}&language=en-US`
		);
		const movieDetail = await response.json();
		console.log('movieDetails>>', movieDetail);
		if (response.ok) {
			return {
				props: {
					// @ts-ignore
					movieDetail
				}
			};
		}
	}
</script>

<script>
	// @ts-nocheck

	export /**
	 * @type {{ backdrop_path: string; }}
	 */
	let movieDetail;
	import { fly } from 'svelte/transition';
</script>

<div class="movie-details" in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 500 }}>
	<img
		src={`https://image.tmdb.org/t/p/original` + movieDetail.backdrop_path}
		alt={movieDetail.title}
	/>
	<div class="text-container">
		<h1>{movieDetail.title}</h1>
		<p class="overview">
			{movieDetail.overview}
		</p>
		<p>
			<span>Release Date</span>{movieDetail.release_date}<br />
			<span>Budget</span>{movieDetail.budget}<br />
			<span>Rating</span>{movieDetail.vote_average}<br />
			<span>Runtime</span>{movieDetail.runtime}<br />
		</p>
	</div>
</div>

<style>
	h1 {
		padding: 1rem 0rem 2rem;
	}

	p {
		padding: 1rem 0rem;
	}

	img {
		width: 100%;
		border-radius: 1rem;
	}

	.movie-details {
		margin: 2rem 20%;
	}
	span {
		font-weight: bold;
	}
</style>
