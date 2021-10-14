<div id="caret">
</div>

<style>
    #caret {
        animation-name: caretFlashSmooth;
        animation: caretFlashSmooth 1s infinite;
        top: 1px;
        left: 5px;
        width: 2px;
        height: 1.5rem;
        /* position: absolute; */
        background: red;
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