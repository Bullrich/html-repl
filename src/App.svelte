<script lang="ts">
	import CodeEditor from "./components/CodeEditor.svelte";
	import Header from "./components/Header.svelte";
	import Renderer from "./components/Renderer.svelte";
	let content: string;

	function onCodeModification(code: CustomEvent<string>) {
		content = code.detail;
	}
</script>

<main>
	<div class="header">
		<Header />
	</div>
	<div class="row">
		<div class="column">
			<CodeEditor bind:content on:change={onCodeModification} />
		</div>
		<div class="column">
			<Renderer {content} />
		</div>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.column {
		float: left;
		width: 50%;
	}

	/* Clear floats after the columns */
	.row:after {
		content: "";
		display: table;
		clear: both;
	}
</style>
