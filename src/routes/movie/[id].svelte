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

	const space = `\u00A0\u00A0\u00A0\u00A0\u00A0`

	const minToHours = (min) => {
		const num = min;
		const hours = num / 60;
		const rhours = Math.floor(hours);
		const minutes = (hours - rhours) * 60;
		const rminutes = Math.round(minutes);

		return space + `${rhours} hour(s) and ${rminutes} minute(s).`;
	};

	const separator = (number) => {
    const str = number.toString().split(".");
    str[0] = str[0].replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    return str.join(".");
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

<div
	class="movie-details"
	in:fly={{ y: 50, duration: 500, delay: 500 }}
	out:fly={{ duration: 500 }}
>
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
			<span>Release Date</span>{space}{movieDetail.release_date}<br />
			<span>Budget</span>{space}${separator(movieDetail.budget)}<br />
			<span>Rating</span>{space}{movieDetail.vote_average}<br />
			<span>Runtime</span>{minToHours(movieDetail.runtime)}<br />
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
