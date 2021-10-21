<script>
	const defaultProps = { text: '', props: {} };

	export let subheading = defaultProps;
	export let heading = defaultProps;
	export let body = defaultProps;
	export let containerProps = {};
	export let footerProps = {};

	// export let body = {}

	// export let subheading = 'Subheading',
	// 	heading = 'Heading',
	// 	body =
	// 		'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Nostrum cumque, dolores dolorem qui commodi numquam at. Neque aspernatur accusamus nobis.';
	// export let headingClass = '',
	// 	subheadingClass = '',
	// 	bodyClass = '',
	// 	containerClass = '',
	// 	containerStyle = 'max-width: 700px;';

	// export let textAlign = 'left';
</script>

<div {...containerProps}>
	<h3 {...subheading.props}>{subheading.text}</h3>
	<h2 {...heading.props}>{heading.text}</h2>
	<p {...body.props}>{body.text}</p>
	<div {...footerProps}><slot /></div>
</div>

<style>
	div > div {
		display: flex;
		flex-wrap: wrap;
		align-items: baseline;
		gap: 1em;

		margin-top: 15px;
	}

	h3 {
		color: var(--gray);
		margin-bottom: 20px !important;
	}

	h2 {
		margin-top: 2px !important;
		color: #616f77 default;
	}
</style>
