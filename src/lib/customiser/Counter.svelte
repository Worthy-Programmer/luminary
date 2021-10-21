<script>
	import { slide } from 'svelte/transition';

	export let body = [];
	export let containerProps = {};
	export let divProps = {};
</script>

<section {...containerProps}>
	{#each body as { title, content }}
		<div {...divProps}>
			{#key content} <h1 transition:slide>{content}</h1> {/key}
			{title}
		</div>
	{/each}
</section>

<style>
	section {
		--h1-size: 2.25rem;
		text-align: center;
		display: flex;
	}

	div {
		flex: 1;
	}

	h1 {
		margin-bottom: 2px;
	}
</style>
