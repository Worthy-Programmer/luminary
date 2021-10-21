<script>
	import InputButtonGroup from './InputButtonGroup.svelte';

	import logo from '/static/img/luminarylogo_1white-01/luminarylogo_1white-01.png';
</script>

<footer>
	<div class="logo">
		<img src={logo} alt="Luminary Logo" />
	</div>

	<section>
		<h3>Features</h3>

		<a href="">Products</a>
		<a href="">Blog</a>
		<a href="">Prompts</a>
	</section>

	<section>
		<h3>Resources</h3>

		<a href=""> About us </a>
		<a href=""> Contact us</a>
		<a href=""> Pricing </a>
		<a href=""> Works cited </a>
	</section>

	<section>
		<h3>More</h3>
		<a href=""> Sign in </a>
		<a href=""> Privacy policy </a>
		<a href=""> Refund policy </a>
	</section>

	<section class="stay-connected">
		<h3>Stay connected</h3>
		<InputButtonGroup inputProps={{ placeholder: 'Email...' }} />
	</section>
</footer>

<style>
	footer {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-evenly;

		background-color: var(--dark-gray);

		--heading-color: white;
		--body-color: white;

		padding: 60px 10px;
	}

	a {
		display: block;
		margin: 5px 0px;
		color: var(--body-color);
		text-decoration: none;
	}

	h3 {
		margin-bottom: 20px;
	}

	.logo {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	@media screen and (max-width: 576px) {
		footer {
			justify-content: space-between;
			padding: 10px 40px;
		}
		section {
			width: 50%;
		}

		section.stay-connected {
			width: 100%;
			/* text-align: center; */
			margin-top: 20px;
		}

		.logo {
			margin: 40px;
		}
	}
</style>
