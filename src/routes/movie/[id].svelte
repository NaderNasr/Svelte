<script context="module">
	//fetch api request
	// @ts-ignore
	export async function load({params}) {
    console.log('params>>',params.id)
		const response = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=${import.meta.env.VITE_API_KEY}&language=en-US`
		);
		const movieDetail = await response.json();
		console.log('movieDetails>>',movieDetail);
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
  export let movieDetail
</script>