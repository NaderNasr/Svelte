<script context="module">
	//fetch api request
	export async function load() {
		const response = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=${
        import.meta.env.VITE_API_KEY
      }`
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
	// exporting popular prop from fetch
	export /**
* @type {any}
*/
	 let popular;
	// console.log(popular)
</script>

<!-- Header -->
<header>
	<a href="/about">About</a>
</header>

<!-- Body  -->
<body>
	<Popular popularMovies={popular} />
</body>
