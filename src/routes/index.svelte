<script context="module">
	//fetch api request
	export async function load() {
		const response = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=${import.meta.env.VITE_API_KEY}`
		);
		const data = await response.json();
		console.log(data);
		if (response.ok) {
			return {
				props: {
					popular: data.results
				}
			};
		}
	}
</script>

<script>
	import Popular from '../components/Popular.svelte';
	import Search from '../components/Search.svelte';
	import { fly } from 'svelte/transition';

	// exporting popular prop from fetch
	export /**
	 * @type {any}
	 */
	let popular;
	// console.log(popular)
</script>

<!-- Body  -->
<body in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 500 }}>
	<Search />
	<Popular popularMovies={popular} />
</body>
