<script>
	import { session } from '$app/stores';

	// Importing styles
	import 'normalizecss/normalize.css';
	import '../styles/global.css';

	// Image loading
	import logoImage from '/static/img/luminarylogo_1white-01/luminarylogo_1white-01@3x.png';
	import listIcon from '/static/img/icons/list.svg';

	import { onMount } from 'svelte';

	function updateScreenSize() {
		$session = { ...$session, screenWidth: screen.availWidth };
	}

	onMount(updateScreenSize);
</script>

<svelte:window on:resize={updateScreenSize} />

<header>
	<div class="left-header">
		<div class="icon">
			<img src={listIcon} alt="" class="" />
		</div>

		<a href="/" class="logo">
			<img src={logoImage} alt="Luminary Logo" class="logo-img" />
		</a>
	</div>

	<nav class="flex ml-auto">
		<div>
			<a href="">Shop Handbooks</a><a href="">Daily Prompt</a><a href="">Works Cited</a><a href=""
				>Works Cited</a
			> <a href="">Blog</a>
		</div>

		<div>
			<a href="">Sign In</a>
			<a href="" class="cart">Cart</a>
		</div>
	</nav>
</header>

<slot />

<style>
	.left-header {
		width: 13vw;
		padding: 15px 40px;

		aspect-ratio: 306/116;

		background-color: var(--orange);

		/* Centering the logo image */
		display: flex;
		justify-content: center;
		align-items: center;

		position: absolute;
		z-index: 20;
		left: 5vw;

		color: white;
	}

	.logo-img {
		display: block;
		margin: auto;

		max-height: 40pt;
	}

	header {
		background-color: var(--gray);

		height: 50pt;
		position: sticky;
		top: 0;

		z-index: 100;
	}

	a {
		text-decoration: inherit;

		color: white;
	}

	nav > div:last-of-type a {
		text-decoration: underline;
	}

	nav {
		height: 100%;
		width: calc(100vw - (18vw + 80px + 40px));
		justify-content: space-evenly;
	}

	nav > div {
		display: flex;
		align-items: center;
		justify-self: center;
		gap: 30px;
	}

	.icon {
		display: none;

		border-right: 1px solid white;
		height: 100%;
		max-width: 75px;

		align-items: center;
		justify-content: center;
	}

	.icon > img {
		height: 30pt;
	}

	@media screen and (max-width: 1000px) {
		nav {
			justify-content: end;
			padding-right: 20px;
			height: 50pt;
		}

		nav > div:first-of-type {
			display: none;
		}

		nav > div:last-of-type a:not(.cart) {
			display: none;
		}

		.left-header {
			height: 50pt !important;
			padding: 0px;
			width: 70vw;
			max-width: 300px;

			min-width: 200;
			display: flex;
			left: 0;
		}

		.logo-img {
			max-height: 30pt;
		}

		.icon {
			display: flex;
			padding: 0px 1px;
			flex: 1;
		}

		.logo {
			flex: 2;
			padding: 0px 4%;
		}
	}
</style>
