<script lang="ts">
    import { onMount } from "svelte";

    import * as wordsJson from "../static/words.english.json";
    import Caret from "./Caret.svelte";
	export let name: string;
    export let keyItems: number[] = [];
    export let totalWords: number = 10;

    onMount(() => {
        for (let i = 0; i < totalWords; i++) {
            // keyItems.push(Math.floor(Math.random() * (200 - 0 + 1) + 0))
            keyItems = [...keyItems, Math.floor(Math.random() * (200 - 0 + 1) + 0)];
        }
        console.log('[keyItems]', keyItems)
        // console.log('[key]', key)
	});

    document.onkeypress = function (event) {
        console.log('[event.key]', event.key)
    }
</script>

<main>
    <Caret />
	<!-- <h1>words here</h1> -->
    <!-- <h2>{wordsJson.words[keyItem]}</h2> -->
    <div class="all-words">
        {#each keyItems as keyItem}
            <h3>{wordsJson.words[keyItem]}</h3>
        {/each}
    </div>
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

    h2, h3 {
        color: #ff3e00;
		text-transform: lowercase;
		font-size: 2em;
		font-weight: 200;
    }
    .all-words {
        display: flex;
        justify-content: space-between;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>