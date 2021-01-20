<script>
	import { Processor } from 'windicss';

	const processor = new Processor();

	let classNames = 'bg-gray-200 font-bold md:font-medium'
	let outputStyle;

	buildStyle();

	function buildStyle() {
		if (classNames.match(/[^:\(-+@]$/)) {
			outputStyle = processor.interpret(classNames).styleSheet.build();
		}
	}
</script>

<main>
	<textarea cols="30" rows="10" on:keyup={buildStyle} bind:value={classNames}/>
	<textarea readonly cols="30" rows="10" bind:value={outputStyle}/>
</main>

<style>
	main {
		width: 100%;
		height: 100%;
		display: flex;
	}

	textarea {
		margin-left: 0.25rem;
		margin-right: 0.25rem;
		width: 50%;
		border-radius: 0.5rem;
	}

	textarea:focus {
		outline-color: #93C5FD;
	}

	@media (max-width: 768px) {
		main {
			flex-direction: column;
		}
		textarea {
			width: 100%;
		}
	}
</style>