<section>
	<div>
		<h1>Banner Title 1</h1>
		<h2>Banner Subtitle 1</h2>
		<p>
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Suscipit illo perferendis numquam
			laborum culpa totam quaerat perspiciatis, deserunt iure cupiditate veritatis odit cum odio?
			Fugit reiciendis sed rem, repellendus modi consequatur et! Voluptates repellendus voluptatem
			laboriosam porro itaque voluptatum facilis!
		</p>
		<button> Button 1 </button>
	</div>
</section>

<style>
	/* The wrapper of the container */
	section {
		--heading-color: white;
		--h1-size: 3.5rem;
		--h2-size: 2rem;
		--body-size: 1.1rem;

		padding: 260px 5vw;

		min-height: 450px;
		height: calc(100vh - 50pt - 50pt);

		color: white;
		background-color: var(--dark-gray);

		position: relative;
		box-sizing: border-box;

		/* Centering div */
		display: flex;
		align-items: center;
	}

	/* Container */
	div {
		max-width: 500px;
	}

	p {
		font-size: var(--body-size);
	}

	h1 {
		margin: 0px;
	}

	h2 {
		font-weight: normal;
	}

	button {
		margin-top: 20px;
	}

	/* Styles for sm */
	@media screen and (max-width: 576px) {
		section {
			--h1-size: 2rem;
			--h2-size: 1.5rem;

			text-align: center;

			height: calc(60vh - 100pt);
		}

		button {
			position: absolute;
			bottom: -15px;

			/* Centering button in y axis */
			left: 50%;
			transform: translateX(-50%);
			width: 50vw;
		}
	}
</style>
