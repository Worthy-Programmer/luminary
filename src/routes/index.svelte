<script context="module">
	export const prerender = true;
</script>

<script>
	import Body from '$lib/home/Body.svelte';
	import Hero from '$lib/home/Hero.svelte';
	import ProductHeader from '$lib/home/ProductHeader.svelte';
	import ContentSnippet from '$lib/home/ContentSnippet.svelte';
	import Tabs from '$lib/home/Tabs.svelte';
	import Accordion from '$lib/home/Accordion.svelte';
	import ShowCase from '$lib/home/ShowCase.svelte';
	import Card from '$lib/home/Card.svelte';
	import EmailBox from '$lib/home/EmailBox.svelte';
	import Footer from '$lib/home/Footer.svelte';

	import blankImg from '/static/img/placeholder_img/blank_img.png';
	import verticalImg from '/static/img/placeholder_img/vertical.png';
	import spiralBoundbookOpen from '/static/img/spiralboundbook-open-01/spiralboundbook-open-01.png';

	import Dropdown from 'svelte-select';

	const contentSnippetPlaceholder = {
		subheading: {
			text: 'Subheading 1',
			props: {
				class: 'cursive'
			}
		},

		heading: {
			text: 'Heading 1 Placeholder'
		},

		body: {
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Alias veniam architecto odio quam, deleniti sunt magni obcaecati dolorum ipsum mollitia?',
			props: {
				style: 'margin: auto;'
			}
		}
	};

	const blogContentSnippetsPlaceholder = {
		...contentSnippetPlaceholder,
		subheading: {
			text: 'BLOG CATEGORY',
			props: {
				style: 'color: var(--orange); font-weight: lighter; font-size: 20px;'
			}
		},
		footerProps: {
			style: 'justify-content: space-between; max-width: 500px;'
		},
		containerProps: {
			style: 'max-width: 600px;'
		},
		body: {
			text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Alias veniam architecto odio quam, deleniti sunt magni obcaecati dolorum ipsum mollitia?',
			props: {
				style: 'text-align: left !important;'
			}
		}
	};
</script>

<ProductHeader />
<Hero />

<!-- Content Snippets -->

<div class="content-snippets container">
	<ContentSnippet contentAlign="left" src={blankImg}>
		<Body {...contentSnippetPlaceholder}>
			<button> Button 2 </button>
			<a href=""> Learn More > </a>
		</Body>
	</ContentSnippet>

	<ContentSnippet>
		<Body {...{ ...contentSnippetPlaceholder, containerProps: { class: 'text-center mx-auto' } }} />
	</ContentSnippet>

	<ContentSnippet src={blankImg}>
		<Body {...{ ...contentSnippetPlaceholder, containerProps: { class: 'text-right' } }} />
	</ContentSnippet>

	<ContentSnippet contentAlign="right" src={verticalImg} imgClass="mh-400">
		<Body {...contentSnippetPlaceholder} />
	</ContentSnippet>

	<ContentSnippet src={blankImg}>
		<Body {...{ ...contentSnippetPlaceholder, containerProps: { class: 'text-right' } }} />
	</ContentSnippet>
</div>

<!-- Image Snippet -->
<div class="image-snippet text-white" style="background-image:url('{spiralBoundbookOpen}');">
	<section class="mx-auto">
		<Body
			{...{
				...contentSnippetPlaceholder,
				containerProps: { style: 'max-width:400px; --heading-color: white;' }
			}}
		>
			<button style="margin-top:30px;"> Button 2 </button>
			<a href=""> Learn More > </a>
		</Body>
	</section>
</div>

<!-- Tabs -->
<section class="text-center">
	<h1>Heading Placeholder</h1>
	<p style="max-width:700px; padding: 30px;" class="mx-auto">
		Lorem, ipsum dolor sit amet consectetur adipisicing elit. Vero, ex! Fugiat placeat dicta cum sed
		obcaecati est et quaerat asperiores.
	</p>

	<Tabs />
</section>

<div class="container mx-auto">
	<Accordion />

	<ShowCase />

	<!-- I want to ... Dropdown -->
	<!-- <div id="i-want-to">
		<h1 class="inline">I want to</h1>
		<Dropdown
			items={['Get Creative']}
			class="i-want-to-dropdown"
			containerStyles={`		
				border-bottom:2px solid var(--gray); 
				float: right; 
				width: 20vw;
				font-family: var(--cursive);
				text-align: center;
				box-sizing: border-box;
				flex: var(--select-container-flex, unset);
			`}
			inputStyles="box-sizing: border-box"
			isClearable={false}
			isSearchable={false}
		/>
	</div> -->

	<!-- The checklist -->
	<!-- <div class="checkmark">
		<div>Lorem ipsum dolor sit.</div>
		<div>Excepturi dicta animi corrupti?</div>
	</div> -->

	<!-- Card layout -->
	<div class="cards">
		<Card
			containerStyles="flex: 1;"
			headerStyles="background-color: var(--dark-gray); color: white;"
		>
			<svelte:fragment slot="headerContent">
				<span>[1]</span> <a href="">View Source</a>
			</svelte:fragment>

			<svelte:fragment slot="bodyContent">
				<h3>Focus your writing</h3>
				<p>
					Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugiat quibusdam, tempora sed
					illum totam quae eaque? Similique ipsam magnam eaque.
				</p>
			</svelte:fragment>
		</Card>

		<Card containerStyles="flex: 1;" headerStyles="background-color: #E2DCD4;">
			<svelte:fragment slot="headerContent">
				<span>[1]</span> <a href="">View Source</a>
			</svelte:fragment>

			<svelte:fragment slot="bodyContent">
				<h3>Focus your writing</h3>
				<p>
					Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt modi nihil laudantium,
					fugit est iure! Totam sit nihil asperiores adipisci, numquam minima quas distinctio est
					rem! Debitis ipsa deleniti harum explicabo architecto facere eos. Error dolor ab obcaecati
					praesentium dicta?
				</p>
			</svelte:fragment>
		</Card>

		<Card containerStyles="flex: 1;" headerStyles="background-color: #EBEDEE;">
			<svelte:fragment slot="headerContent">
				<span>[1]</span> <a href="">View Source</a>
			</svelte:fragment>

			<svelte:fragment slot="bodyContent">
				<h3>Focus your writing</h3>
				<p>
					Lorem ipsum dolor sit amet consectetur adipisicing elit. Pariatur fugit sapiente quaerat
					possimus dignissimos itaque aperiam vitae deserunt voluptas maxime quos? Commodi mollitia
					assumenda sequi adipisci recusandae deserunt magnam,
				</p>
				<p>
					doloribus cumque deleniti reprehenderit similique cupiditate tempore ipsa in minus ex
					dolor nemo qui unde saepe id suscipit? Error asperiores consectetur mollitia similique,
					vitae ducimus expedita.
				</p>
			</svelte:fragment>
		</Card>
	</div>

	<!-- Email Box -->
	<EmailBox />

	<!-- BLOG -->
	<ContentSnippet>
		<Body {...blogContentSnippetsPlaceholder}>
			<span>30 min read</span>
			<span>Dec 14, 2020</span>
		</Body>
	</ContentSnippet>

	<ContentSnippet
		src={blankImg}
		figCaption="Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facere, facilis?"
		containerProps={{ style: 'align-items: start;' }}
		bodyContainerProps={{ style: 'flex:3;' }}
	>
		<Body
			{...{ ...blogContentSnippetsPlaceholder, containerProps: { style: 'text-align: center' } }}
		/>
	</ContentSnippet>
</div>

<Footer />

<style>
	section {
		padding-top: 40px;
		padding-bottom: 40px;
	}
	.content-snippets {
		margin: 20px auto;
	}

	.cards {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
		align-items: start;

		gap: 40px 40px;

		margin: 100px 0px;
	}

	.image-snippet {
		padding: 10vw;
		background-color: var(--dark-gray);

		background-position: 400px -400px;
		background-repeat: no-repeat;
	}

	#i-want-to {
		--border: 0px;
		--borderRadius: 0px;

		--heading-color: var(--gray);

		display: flex;
		justify-content: end;
		align-items: center;
	}

	.checkmark {
		/* display: inline; */
		width: 20vw;
		margin-left: auto;
	}

	.checkmark > div {
		padding-top: 10px;
	}

	@media screen and (max-width: 576px) {
		#i-want-to {
			justify-content: center;

			--select-container-flex: 1;
		}

		.checkmark {
			width: 50%;

			/* margin: auto; */
		}
	}
</style>
