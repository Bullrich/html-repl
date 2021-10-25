<script lang="ts">
    import { createEventDispatcher, onMount } from "svelte";

    const dispatch = createEventDispatcher();
    export let content: string = `<html>
    <body>
        <h1>HTML REPL</h1>
        <h3>This is a html repl</h3>
        <p style="color: red"> It even supports <span class="blue">CSS</span>
    </body>
    <style>
        .blue { color: blue }
        h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	    }
    </style>
</html>`;

    function onInput(event: Event) {
        const target = <HTMLTextAreaElement>event.target;
        content = target.value;
        dispatch("change", target.value);
    }
</script>

<div>
    <p>
        Visit the <a href="https://www.w3schools.com/html/">W3 Schools</a> to learn
        how to build websites.
    </p>
    <textarea value={content} id="editor" on:input={onInput} />
</div>

<style>
    textarea {
        width: 50%;
        min-height: 500px;
    }
</style>
