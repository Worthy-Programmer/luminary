<script>
	import { createEventDispatcher, onMount } from 'svelte';

	export let options;

	export let activeIndices = [0];
	const dispatch = createEventDispatcher();

	export let containerProps = {};
	export let optionProps = {};
	export let activeOptionProps = {};

	export let isRadio = true;

	let activeOptions =  new Set([])

	function changeOption(index) {
		if (isRadio) {
			const activeIndex = activeIndices[0]
			options[activeIndex].isActive = false;
			options[index].isActive = true;

			activeIndices = [index]
			dispatch('change', options[index]);
			return;
		}

		const option = options[index]
		options[index].isActive = !option.isActive;

		if(!option.isActive) {
			activeOptions.add(options[index])
		} else {
			activeOptions.delete(options[index])
		}
		dispatch('change', activeOptions);

	}

	function setActiveOptions() {
		activeOptions = new Set(activeIndices.map(index => {
			options[index].isActive = true;
			return options[index]
		}))
	}

	onMount(setActiveOptions)
</script>

<section {...containerProps}>
	{#each options as {heading, body, isActive}, index}
		<div
			{...optionProps}
			{...(isActive ? activeOptionProps : {})}
			class:active={isActive}
			on:click={() => changeOption(index)}
		>
			{#if heading} <h5>{heading}</h5> {/if}
			{#if body} <p>{body}</p> {/if}
		</div>
	{/each}
</section>

<style>
	section {
		display: flex;
		border-radius: var(--border-radius, 100px);
		background-color: var(--light-gray);
		padding: 7px 10px;
	}

	div {
		flex: 1;
		text-align: center;
		border-radius: var(--border-radius, 100px);
		padding: 7px 4px;
		margin: 0px 3px;
	}

	h5,
	p {
		margin: 0px;
	}

	.active {
		background-color: var(--active-bg-color, #fff) !important;
		border: var(--active-border-color, 2px solid #007dcf) !important;
	}
</style>
