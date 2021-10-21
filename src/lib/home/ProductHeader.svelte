<header class="mx-auto">
	<div class="header ml-auto">
		<h3 class="bold flex-1">journal</h3>
		<!-- svelte-ignore a11y-invalid-attribute -->
		<a href="" class="link">Overview</a>
		<!-- svelte-ignore a11y-invalid-attribute -->
		<a href="" class="active link">Specs</a>
		<!-- svelte-ignore a11y-invalid-attribute -->
		<a href="" class="active link">Compare</a>
		<button>Button</button>
	</div>
</header>

<style>
	header {
		background-color: #fff;
		position: sticky;

		/* Height of navbar */
		top: 50pt;
		z-index: 10;
		height: 50pt;
		/* box-sizing: border-box; */

		display: flex;
		align-items: center;
		justify-content: stretch;

	}

	.header {
		display: flex;
		justify-content: space-around;
		align-items: baseline;

		color: #a7b5bb;
		font-size: 1.1rem;

		/*  Removing the left side of the block, which is covered by the logo */
		width: calc(100vw - (18vw + 80px + 60px + 80px));

		gap: 0rem 4rem;
				padding-right: 80px;

	}

	h3 {
		font-size: 20pt;
		flex: 1;
		color: #a7b5bb;
	}

	/* .header > div {
		display: flex;
		justify-content: space-around;
		align-items: baseline;
		flex: 1;

		color: #c7cdcf;
	} */

	.active {
		color: var(--dark-gray);
	}

	a {
		text-decoration: inherit;
	}

	@media screen and (max-width: 1000px) {
		.header {
			width: 90%;
			margin: 0px auto;

			justify-content: space-around !important;
			padding-right: 0px;
			gap: 0rem 1rem;
		}

		header {
			width: 100vw;
						max-width: 100vw;

		}

		h3 {
			flex: unset;
		}

		a.link {
			display: none;
		}
	}
</style>
