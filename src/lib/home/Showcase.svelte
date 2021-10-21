<script>
	import { session } from '$app/stores';

	import { onMount } from 'svelte';

	import Dropdown from 'svelte-select';

	export let data = {
		planner: {
			img: '',
			price: 45.99,
			url: '#',

			'Great for': `Lorem, ipsum dolor sit amet consectetur adipisicing elit. Culpa, et consequatur. Officiis sequi quidem a nam perferendis omnis reiciendis! Quia.`
		},
		notebook: {
			img: '',
			price: 35.99,
			url: '#',
			'Great for': `Lorem, ipsum dolor sit amet consectetur adipisicing elit. Culpa, et consequatur. Officiis sequi quidem a nam perferendis omnis reiciendis! Quia.`
		},
		journal: {
			img: '',
			price: 35.99,
			url: '#',
			'Great for': `Lorem, ipsum dolor sit amet consectetur adipisicing elit. Culpa, et consequatur. Officiis sequi quidem a nam perferendis omnis reiciendis! Quia.`
		}
	};

	const Objectkeys = Object.keys(data);

	export let items = Objectkeys.map((key) => {
		return {
			value: key,
			label: key
		};
	});

	let visibleColumns = [Objectkeys[0], Objectkeys[1], Objectkeys[2]];

	export let visibleRows = ['Great for'];

	session.subscribe((session) => {
		if (session.screenWidth < 670) {
			visibleColumns = [Objectkeys[0], Objectkeys[1]];
			console.log(visibleColumns);
		} else {
			visibleColumns = [Objectkeys[0], Objectkeys[1], Objectkeys[2]];
		}
	});
</script>

<div class="flex header">
	{#each visibleColumns as key, index}
		<section class="flex-1 text-center">
			<Dropdown
				{items}
				value={key}
				on:select={(e) => {
					visibleColumns[index] = e.detail.value;
				}}
				isClearable={false}
				isSearchable={false}
			/>

			<img src={data[key].img} alt="" />

			<h2>$ {data[key].price}</h2>

			<button href={data[key].url} class="block mx-auto"> Button </button>
		</section>
	{/each}
</div>
<div class="flex footer">
	<!-- .flex -->
	{#each visibleRows as row}
		<h3>{row}</h3>

		{#each visibleColumns as key}
			<p class="flex-1">{data[key][row]}</p>
		{/each}
	{/each}
</div>

<style>
	div.flex {
		gap: 10px 30px;
				--inputPadding: 0px !important;

	}

	.header {
		margin-top: 100px;
	}

	.footer {
		flex-wrap: wrap;
		margin-bottom: 100px;
	}

	h3 {
		width: 100%;
		padding: 10px 0;
		border-bottom: 1px solid var(--border-color);
	}

	@media screen and (min-width: 576px) {
		h3 {
			transform: translateX(-120px);
			min-width: calc(100% + 120px);
			margin: 40px 60px 0px 60px;
		}
	}
</style>
