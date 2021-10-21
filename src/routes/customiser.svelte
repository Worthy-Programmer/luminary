<script>
	import Counter from '$lib/customiser/Counter.svelte';
	import SwitchRadio from '$lib/customiser/Switch.svelte';
	import StarRating from '$lib/StarRating.svelte';
	import Modal from '$lib/Modal.svelte';

	// Third Party
	import Carousel from 'svelte-carousel';

	// Static Assets
	import trainerImg from '/static/img/customiser/trainer.webp';
	import chevronDown from '/static/img/icons/chevron-down.svg';
	import { onMount } from 'svelte';

	const counterBody = [
		{
			title: 'Pages',
			content: 180
		},
		{
			title: 'Months',
			content: 3
		},
		{
			title: 'Days',
			content: 90
		}
	];

	const switchOptions = [
		{
			heading: 'Fitness & Nutrition',
			body: '90 days'
		},

		{
			heading: 'Fitness Only',
			body: '180 days'
		}
	];

	function changeCounter({ detail: option }) {
		if (option.heading == 'Fitness Only') {
			counterBody[1].content = 2;
		} else counterBody[1].content = 3;

		counterBody[2].content = counterBody[1].content * 30;

		console.log(option.heading);
	}

	let chooseFocusModal = false;
	let chooseFocusModalParagraph = ""

	let chosenTrainingFocus;

	const trainingFocus = [
		{
			heading: 'Self Care',
			subheading: 'Part 1',
			body: 'Practice self-compassion. Reduce distractions and improve clarity.',
			mostPopular: true,
			img: ''
		},

		{
			heading: 'Focus',
			mostPopular: false,
			img: '',
			body: ''
		},

		{
			heading: 'Mindfulness',
			mostPopular: true,
			img: '',
			body: ''
		},

	];

	let modalCarousel;
</script>

<div id="page" class="container mx-auto">
	<div id="book">e</div>
	<div id="customiser">
		<img src={trainerImg} alt="trainer" class="trainer-img" />

		<div id="review-flex" class="remove-my">
			<div class="star-rating">
				<StarRating
					style={{ styleFullStarColor: '#E5BD5E', styleStarWidth: 20 }}
					isIndicatorActive={false}
				/>
			</div>
			<a href="">Reviews</a>
			<h2>$39.90</h2>
		</div>

		<Counter body={counterBody} containerProps={{ style: 'max-width: 500px;' }} />

		<div>
			<h2>Training Focus</h2>
			<p>Choose your sport or training focus</p>

			<div class="choose-focus" on:click={() => (chooseFocusModal = !chooseFocusModal)}>
				<div> 
					{#if chosenTrainingFocus}
					{chosenTrainingFocus?.heading}
					{/if}
				</div>
				<img src={chevronDown} alt="Choose training focus" />
			</div>
		</div>

		<div>
			<p>Would you like to track your nutrition?</p>
			<SwitchRadio options={switchOptions} on:change={changeCounter} />
			<p>Both options equal a total amount of 180 pages</p>
		</div>

		<div>
			<h2>Daily Pages</h2>
			<p>Pick a layout you like, then edit your daily page layout.</p>
		</div>
		<div>
			<h2>Calendars</h2>
			<p>Which calendars would you like in your 3-month book?</p>
			<SwitchRadio
				isRadio={false}
				options={[{ heading: 'Monthly Calendar' }, { heading: 'Weekly Calendar' }]}
				containerProps={{ style: 'background-color: white;' }}
				optionProps={{
					style: 'padding-top: 15px; padding-bottom: 15px; border: 1px solid var(--border-color);'
				}}
			/>
			<p>You may select more than one if you like.</p>
		</div>

		<div>
			<h2>Page Numbers</h2>
			<SwitchRadio
				options={[{ heading: 'Yes' }, { heading: 'No' }]}
				optionProps={{ style: 'padding-top: 15px; padding-bottom: 15px;' }}
			/>
		</div>
		<div>
			<h2>Review</h2>
			<p>Please review your book.</p>
			<p>You can get started immediately with a free, one-week, print-at-home version.</p>
		</div>
	</div>
</div>

{#if chooseFocusModal}
	<Modal on:close={() => (chooseFocusModal = false)}>
		<div class="text-center">
			<p>Hover to learn more</p>
			<Carousel bind:this={modalCarousel} particlesToShow={3} particlesToScroll={1}>
				{#each trainingFocus as focus}
					<div>

						<div class="training-focus" 
						class:active={focus.mostPopular}
						on:click={() => {
							chosenTrainingFocus = focus;
							chooseFocusModal = false;
						}}
						on:mouseover={() => chooseFocusModalParagraph = focus.body} on:focus={() => chooseFocusModalParagraph = focus.body}>
							<img src={focus.img} alt="" />
							<h4>{focus.heading}</h4>
							 <h6>{focus.subheading ?? ''}</h6> 
						</div>
					</div>
				{/each}
			</Carousel>
			<p>{chooseFocusModalParagraph}</p>
		</div>
	</Modal>
{/if}

<style>
	:global(body) {
		max-height: 100vh;
	}

	/* Setup */
	#page {
		display: flex;
		flex-wrap: wrap;

		--container-width-lg: 80%;
		--container-width-xl: 80%;
		--container-width-xxl: 80%;

		padding: 20px;
	}

	#book {
		flex: 3;
	}

	#customiser {
		flex: 2;
		padding: 20px;

		overflow-y: scroll;


	}




	/* Trainer Image */
	.trainer-img {
		max-width: 200px;
		margin-bottom: 10px;
	}

	#review-flex {
		display: flex;
		align-items: center;
	}

	#review-flex > h2 {
		max-width: 200px;
		flex: 1;
		text-align: right;
	}

	.star-rating {
		width: 150px;
		height: 20px;
		overflow-y: hidden;
		/* display: inline; */
	}

	#customiser > div:not(.remove-my) {
		margin-top: 50px;
		margin-bottom: 50px;
	}

	.choose-focus {
		display: flex;
		gap: 0px 10px;
	}

	.choose-focus > div {
		height: 150px;
		aspect-ratio: 1;
		border-radius: 25px;

		border: 3px solid #a7b5bb;

		/* display: inline; */
	}

	.choose-focus > img {
		width: 25px;
	}

	.training-focus {
		aspect-ratio: 1;
		display: flex;
		flex-direction: column;
		justify-content: center;
		border: 1px solid var(--border-color);
		margin: 30px 30px;
				border-radius: 35px;

	}

	.training-focus:hover , .training-focus.active {
		border-width: 3px;
		box-shadow:  1px 1px 10px #00000029;
		transform: translateY(-10px);
	}

	.training-focus > * {
		margin: 4px 0px  !important;
	}


	@media screen and (max-width: 1000px) {
		#page{
			display: block;
		}

		#customiser > * {
			/* width: 90%; */
			margin: auto;
		}}
	
</style>
