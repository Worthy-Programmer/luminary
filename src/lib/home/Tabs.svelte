<script>
	import spiralBoundbookOpen from '/static/img/spiralboundbook-open-01/spiralboundbook-open-01.png';

	export let data = {
		'Self Care': `
	<div class="flex" style="position: relative; flex-wrap: wrap;">
		 <div style=""> 
				<h2> Placeholder </h2>
				<p >Choose a pathway to focus your journal around.</p>
				 <a href="#"> Learn More > </a> </div> 

               <div class="flex-1"> 
                <img src="${spiralBoundbookOpen}" 
                class="spiralbook-img"/> 
                </div>
			 </div>

              `,

		Gratitude: ' <p>Gratiude.</p> <a href="#"> Learn More > </a> ',

		Mindfulness: ' <p>Mindfulness</p> <a href="#"> Learn More > </a> ',

		Empathy: ' <p>Empathy</p> <a href="#"> Learn More > </a> '
	};

	export let active = 0;
</script>

<!-- 
	<div class="flex" style="position: relative;">
		 <div style="min-width:50vh;"> 
				<h2> Placeholder </h2>
				<p >Choose a pathway to focus your journal around.</p>
				 <a href="#"> Learn More > </a> </div> 

               <div class="flex-1"> 
                <img src="${spiralBoundbookOpen}" 
                style="position: absolute; top: -450px; left: 200px; transform: rotate(15deg)" /> 
                </div>
			 </div>  -->

<hgroup>
	{#each Object.keys(data) as heading, index}
		<h5 class:active={index === active} on:click={() => (active = index)}>
			<button type="button"> {heading} </button>
		</h5>
	{/each}
</hgroup>

<div class="container mx-auto text-left">
	{#each Object.values(data) as body, index}
		<div class="body {active === index ? 'block fade-in' : 'hidden'}">{@html body}</div>
	{/each}
</div>

<style>
	hgroup {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		align-items: baseline;
		gap: 14px 5vw;

		position: relative;
		top: 50px;
		z-index: 5;

		/* Changing h3 size */
		/* --h5-size: --h4-size; */
	}

	h5 > button {
		font-weight: lighter;

		color: inherit;
		background-color: #fff;

		border: 2pt solid var(--border-color);
	}

	h5.active > button {
		border-width: 0px;
		background-color: var(--dark-gray);

		color: white;
	}

	div.container {
		background-color: #ebedee;
		padding: 100px;

		overflow-x: unset;
		overflow-y: hidden;
		overflow-y: -moz-hidden-unscrollable;

		box-sizing: border-box;
	}

	:global(.spiralbook-img) {
		position: absolute;
		top: -28rem;
		left: 3vw;
		/* top: -450px;
		left: 200px; */
		transform: rotate(15deg);
	}

	@media screen and (max-width: 576px) {
		div.container {
			padding: 30px;
		}

		h5 {
			margin: auto;
		}

		hgroup {
			position: static;
			margin-bottom: 20px;
		}


	}

		@media screen and (max-width: 700px) {

			:global(.spiralbook-img) {
			position: static;

			max-width: 100%;
			min-width: 200px;
		}
	}
</style>
