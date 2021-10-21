<script>
	import { session } from '$app/stores';
	import {onMount} from 'svelte'
	// import Carousel from 'svelte-carousel'
 let Carousel;
		onMount(async () => {
    const module = await import('svelte-carousel');
    Carousel = module.default;
  });

	import { slide } from 'svelte/transition';
	import spiralBoundbookOpen from '/static/img/spiralboundbook-open-01/spiralboundbook-open-01.png';

	export let data = [
		 {
			 heading: 'Focus your writing',
			body: ` <p> Lorem ipsum dolor sit amet consectetur, adipisicing elit. Quis, cupiditate! </p> <a href="#"> Learn More > </a>`,
			img: spiralBoundbookOpen,
			imgStyle: 'transform: rotate(19deg); '
		},
		 {
			heading: 'Develop or break habits',
			body: '<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus dicta excepturi impedit itaque vitae quas sequi hic maxime quod a?</p>',
			img: spiralBoundbookOpen
		},
		{
			heading: 'Write freeform',
			body: '<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus dicta excepturi impedit itaque vitae quas sequi hic maxime quod a?</p>',
			img: spiralBoundbookOpen
		},
		 {
			 heading: 'Room to doodle',
			body: '<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus dicta excepturi impedit itaque vitae quas sequi hic maxime quod a?</p>',
			img: spiralBoundbookOpen
		},
		 {
			 heading: 'Get Inspired',
			body: '<p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus dicta excepturi impedit itaque vitae quas sequi hic maxime quod a?</p>',
			img: spiralBoundbookOpen
		}
	];

	export let active = 0;
	let carouselBind;
</script>

<div class="flex main mx-auto">
	<div class="flex-1 accordion">
		{#if $session.screenWidth >= 576}
		{#each data as section, index}
			<section class:active={active === index} on:click={() => (active = index)}>
				<h3>{section.heading}</h3>

				{#if active === index}
					<p transition:slide>{@html section.body}</p>
				{/if}
			</section>
		{/each}
		{:else}
		<svelte:component 
		this={Carousel} 
		bind:this={carouselBind}
		on:pageChange={e => active = e.detail}
		>
				{#each data as {heading, body}, index}
			<section class:active={active === index} on:click={() => (active = index)}>
				<h3>{heading}</h3>

					<p>{@html body}</p>
			</section>
		{/each}
		</svelte:component>
		{/if}
	</div>

	<div class="flex-2 w-full-at-sm">
		<img src={data[active].img} alt="" style={data[active].imgStyle ?? ''} class="block mr-auto" />
	</div>
</div>

<style>
	section {
		--heading-color: #ced3d5;
		--body-color: #ced3d5;

		border-left: 1px solid var(--border-color);
		padding: 1px 40px 1px 20px;
		margin: 30px 0px;
	}

	section.active {
		--heading-color: inherit;
		--body-color: inherit;

		border-left: 4pt solid var(--orange);
	}

	img {
    min-width: 300px;
    max-width: 80vw;
    margin: auto;
    width: 100%;
}
	

	p {
		max-height: 200px;
	}

	div.main > div {
		order: 2;
	}
	div.main {
		flex-wrap: wrap;
		justify-content: space-between;
		margin: 50px auto;
	}

	@media screen and (max-width: 576px) {
		.w-full-at-sm {
			width: 100%;
			order: 1 !important;
		}

		.accordion {
			width: 80vw;
			display: flex;
			margin: auto;
		}


		section {
			--heading-color: inherit;

			padding: 0px; 
		
			/* width: 100%; */
			border: none !important;
		}

		
	}
</style>

