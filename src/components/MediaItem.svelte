<!-- https://linguinecode.com/post/how-to-pass-children-elements-in-svelte -->
<style>
    .sound-container {
        text-align:center;
        width:100%;
        display: grid;
        grid-template-columns: auto auto;
        grid-template-rows: auto;
        padding-top: 0.5em;
        padding-bottom: 0.5em;
    }
    .writing {
        padding-left: 1em;
        text-align: left;
    }

</style>

<div class="sound-container">
    <slot name="media">
        <iframe title="some-media" class="item-media"></iframe>
    </slot>
    <div class="writing">
        <slot name="description"><p class="item-desc"></p></slot>
    </div>
</div>