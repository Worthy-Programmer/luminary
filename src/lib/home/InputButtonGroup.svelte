<script>
	import { createEventDispatcher } from 'svelte';

	export let containerProps = {};
	export let inputProps = { type: 'text' };
	export let buttonProps = {};
	export let buttonTextContent = 'Button';

	const dispatch = createEventDispatcher();
	let inputValue;

	function dispatchInputValue() {
		dispatch('submit', inputValue);
	}
</script>

<form {...containerProps} on:submit|preventDefault={dispatchInputValue}>
	<input class="flex-1" {...inputProps} bind:value={inputValue} />
	<button type="submit" {...buttonProps}> {buttonTextContent}</button>
</form>

<style>
	form {
		display: flex;
		justify-content: space-evenly;
		/* align-items: baseline; */
		background-color: white;

		padding: 10px 10px;

		border-radius: 300px;
	}

	input {
		background-color: inherit;
		border: 0px;
		padding-left: 20px;
	}

	button {
		margin: 0px 1px;
	}

	@media screen and (max-width: 576px) {
		input {
			width: 90%;
		}
	}
</style>
