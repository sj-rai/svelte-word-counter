<script lang="ts">
    export const move = (): void => {
        document.getElementById("caret").animate(
        {
            // top: firstLetter.offsetTop - $(firstLetter).height() / 4,
            // left: firstLetter.offsetLeft,
            top: '10px',
            left: '10px',
        },
        0,
        // "linear"
        )
    }
</script>

<div id="caret">
</div>

<style>
    #caret {
        animation-name: caretFlashSmooth;
        animation: caretFlashSmooth 1s infinite;
        top: 1px;
        left: 5px;
        width: 2px;
        height: 1.9rem;
        /* position: absolute; */
        background: #ff3e00;
        /* background-color: red; */
        border-radius: 10px;
    }
    @keyframes caretFlashSmooth {
        0%,
        100% {
            opacity: 0;
        }
        50% {
            opacity: 1;
        }
    }
</style>