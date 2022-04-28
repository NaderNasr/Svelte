<script>
	let inputValue = '';
	let active = false;
	import { goto } from '$app/navigation';
	const isInactive = () => {
		if (inputValue) {
			active = true;
		} else {
			active = false;
		}
	};

	const submitSearch = () => {
		goto('/search/' + inputValue);
	};
</script>

<form on:submit|preventDefault={submitSearch} class="search">
	{#if !inputValue}
		<label for="search">Search Movie</label>
	{/if}
	<input
		onblur={isInactive}
		on:focus={() => (active = true)}
		bind:value={inputValue}
		name="search"
		type="text"
		class={active ? 'selected' : ''}
	/>
	{#if inputValue}
		<button>Search</button>
	{/if}
</form>

<style>
	.search {
		position: relative;
		width: 30%;
		margin: 1rem;
	}

	input {
		width: 100%;
		border: none;
		font-size: 1rem;
		outline: none;
		color: rgb(255, 255, 255);
		padding: 0.5rem 1rem;
		transition: background 0.75s ease-out;
		font-weight: bold;
		background: rgb(63, 63, 63);
		border-radius: 10px;
		padding: 1rem;
	}

	label {
		position: absolute;
		font-size: 0.8rem;
		top: 50%;
		left: 0;
		transform: translate(0, -50%);
		pointer-events: none;
		color: #fff;
		padding: 0rem 1rem;
	}

	button {
		font-size: 0.7rem;
		padding: 0rem 1rem;
		background: rgb(96, 110, 201);
		color: white;
		font-weight: bold;
		border: none;
		position: absolute;
		bottom: 50%;
		right: 0;
		transform: translate(0, 50%);
		height: 100%;
		border-top-right-radius: 10px;
		border-bottom-right-radius: 10px;
		cursor: pointer;
	}

	input.selected {
		background: rgb(50, 50, 50);
	}
</style>
