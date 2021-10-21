<script>
	import { createEventDispatcher } from 'svelte';

	import InputButtonGroup from './InputButtonGroup.svelte';

	export let textareaProps = {};
	export let InputButtonGroupProps = {
		containerProps: {
			style: 'max-width: 350px; width: 90%; ',
			class: 'ml-auto'
		},

		inputProps: {
			placeholder: 'Email...',
			type: 'email'
		},

		buttonTextContent: 'Submit'
	};

	let textareaValue;
	const dispatch = createEventDispatcher();

	function dispatchTextareaValueAlongWithEmail({ detail: email }) {
		dispatch('submit', { textarea: textareaValue, email });
	}
</script>

<fieldset>
	<textarea {...textareaProps} bind:value={textareaValue} />
	<InputButtonGroup {...InputButtonGroupProps} on:submit={dispatchTextareaValueAlongWithEmail} />
</fieldset>

<style>
	fieldset {
		/* max-width: 50%; */
		padding: 25px;
		background-color: #ebedee;
		border-radius: 20px;

		/* margin */

		box-sizing: border-box;
	}

	textarea {
		width: 100%;
		border-radius: 20px;
		border: 0px;

		padding: 20px;

		min-height: 200px;
		margin-bottom: 20px;

		box-sizing: border-box;
	}

	@media screen and (max-width: 576px) {
		textarea {
			padding: 21px;
		}

		fieldset {
			padding: 10px;
		}
	}
</style>
