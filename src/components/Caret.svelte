<script lang="ts">
    let caretMove = false
    export const move = (): void => {
        caretMove = true;
        // document.getElementById("caret").animate([
        // // keyframes
        // { transform: 'translateX(0px)' },
        // { transform: 'translateX(10px)' }
        // ], {
        // // timing options
        // duration: 150,
        // iterations: 1
        // })
    }
</script>

<div id="caret" class:caretMove >
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

    .caretMove {
        animation-name: moveAnimate !important; /* to override the #caret, !important*/
        animation-duration: 150;
        animation-iteration-count: 1;
        animation-timing-function: ease;
        animation-fill-mode: forwards;
    }

    @keyframes moveAnimate {
        from {
            transform: translateX(0px)
        }
        to {
            transform: translateX(10px)
        }
    }
</style>