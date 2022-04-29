<script>
	let inputValue = '';
	let active = false;
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

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
		<label in:fly={{ y: -10, duration: 500 }} out:fly={{ y: -10, duration: 500 }} for="search">Search Movie</label>
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
		<button in:fly={{ x: 10, duration: 500 }} out:fly={{ y: 0, duration: 500 }}>Search</button>
	{/if}
</form>

<style>
	.search {
		position: relative;
		width: 100%;

	}

	input {
		width: 100%;
		border: none;
		font-size: 1rem;
		outline: none;
		color: rgb(255, 255, 255);
		padding: 0.5rem 1rem;
		font-weight: bold;
		background: rgb(0, 0, 0);
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
		background: rgb(0, 0, 0);

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
		background: rgb(0, 0, 0);
	}
</style>
