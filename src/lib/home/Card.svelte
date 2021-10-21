<script>
	export let containerStyles = '';
	export let headerStyles = '';
	export let bodyStyles = '';
</script>

<section style={containerStyles}>
	<div class="header" style={headerStyles}>
		<slot name="headerContent" />
	</div>
	<div class="body" style={bodyStyles}><slot name="bodyContent" /></div>
</section>

<style>
	.header {
		display: flex;
		justify-content: space-between;
		align-items: center;

		padding: 20px 30px;
		border-top-left-radius: var(--border-radius);
		border-top-right-radius: var(--border-radius);
	}

	.body {
		padding: 15px 20px;
		--heading-color: var(--gray);

		border-bottom-left-radius: var(--border-radius);
		border-bottom-right-radius: var(--border-radius);
	}

	section {
		--border-radius: 22pt;

		border: 1px solid #00000029;
		border-radius: var(--border-radius);

		box-shadow: 0px 8pt 15px #00000029;

		min-width: 200px;
	}
</style>
