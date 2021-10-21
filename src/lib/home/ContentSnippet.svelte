<script>
	export let src = '',
		contentAlign = 'left';
	export let imgClass = '';

	export let figCaption = '';

	export let bodyContainerProps = {};
	export let containerProps = {};
</script>

<section {...containerProps}>
	<div class="flex-1 order-2" {...bodyContainerProps}>
		<slot />
	</div>

	{#if src !== ''}
		<figure class={contentAlign === 'left' ? 'order-2' : 'order-1'}>
			<img
				{src}
				alt=""
				class="{imgClass} {contentAlign === 'right'
					? 'ml-auto'
					: contentAlign === 'left'
					? 'mr-auto'
					: 'mx-auto'}"
			/>
			<figcaption>{figCaption}</figcaption>
		</figure>
	{/if}
</section>

<style>
	section {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		align-items: center;

		color: var(--dark-gray);

		margin: 70px auto;
		gap: 5em;
	}

	img {
		border-radius: 15pt;
		box-shadow: 0px 8pt 6pt #00000029;
		max-width: 100%;
		min-width: 230px;

		display: block;
	}

	figure {
		flex: 1;
		margin: 0;
	}

	figcaption {
		margin-top: 20px;
	}

	/* Styles for sm */
	@media screen and (max-width: 576px) {
		img {
			margin: auto;
		}
	}
</style>
