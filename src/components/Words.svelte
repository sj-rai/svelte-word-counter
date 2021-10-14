<script lang="ts">
import { onMount } from "svelte";

    import * as wordsJson from "../static/words.english.json";
	export let name: string;
    export let keyItem: integer;

    onMount(() => {
		keyItem = Math.floor(Math.random() * (200 - 0 + 1) + 0)
        // console.log('[key]', key)
	});
</script>

<main>
	<h1>words here</h1>
    <h2>{wordsJson.words[keyItem]}</h2>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>