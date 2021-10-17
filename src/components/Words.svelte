<script lang="ts">
    import { onMount } from "svelte";

    import * as wordsJson from "../static/words.english.json";
    import Caret from "./Caret.svelte";
    let caretInstance: Caret = null;
    export let keyItems: number[] = [];
    export let totalWords: number = 10;
    export let currentLetter: number|string = '', allLeters: string[] = [], currentIndex: number = 0;
    export let pressedKeys: string[] = []

    onMount(() => {
        for (let i = 0; i < totalWords; i++) {
            // keyItems.push(Math.floor(Math.random() * (200 - 0 + 1) + 0))
            keyItems = [...keyItems, Math.floor(Math.random() * (200 - 0 + 1) + 0)];
        }
        keyItems.forEach((item) => {
            let currentWord = wordsJson.words[item]
            for(let i = 0; i < currentWord.length; i++) {
                allLeters.push(currentWord.substring(i,i+1))
            }
            allLeters.push(' ');
            // allLeters.push(currentWord.substring(0,1))
        })
        currentLetter = allLeters[currentIndex]
        // console.log('[key]', key)
	});

    document.onkeypress = function (event: KeyboardEvent) {
        if((currentLetter === event.key) || (event.keyCode === 32 && currentLetter === ' ')) {
            console.log('[correct]')
            currentLetter = moveNext()
            // if correct, update current element

        } else {
            console.log('[wrong]')
        }
        pressedKeys = [...pressedKeys, event.key]
        caretInstance.move();
    }

    let moveNext = (): string => {
        currentIndex = ++currentIndex;
        return allLeters[currentIndex];
        // return ''
    }
</script>

<main>
    <div class="caret">
        <Caret bind:this={caretInstance}/>
    </div>
    <div class="all-words-pressed">
        {#each pressedKeys as pressedKey}
            <h3>
                <pre>{pressedKey}</pre>
            </h3>
        {/each}
    </div>
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

    /* pre {

    } */

    .all-words {
        display: flex;
        justify-content: space-between;
    }
    .all-words-pressed {
        display: flex;
    }

    .caret {
        position: absolute;
        top: 340px;
        left: 38px;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>