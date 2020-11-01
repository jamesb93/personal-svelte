<!-- https://daveceddia.com/svelte-with-sass-in-vscode/ -->
<!-- https://stackoverflow.com/questions/32378953/keep-the-middle-item-centered-when-side-items-have-different-widths -->
<!-- https://css-tricks.com/full-bleed/ -->

<script>
	import StaticNav from "../components/StaticNav.svelte"
	import { fade } from 'svelte/transition';
	import { onMount } from "svelte";	
	export let segment;
	let w;
	let navshow = false;

	function clickHandle() {
		navshow = !navshow;
	}
</script>

<style>
/* Grid */
	.wrapper {
		display: grid;
		grid-template-columns: auto min(85ch, 100%) auto;
		justify-content: center;
		padding-left: 0em;
		padding-right: 0em;
		max-width: 130ch;
		margin: 0 auto;
	}

	.wrapper > * {grid-column: 2;}

	.content {
		margin-top: 5em;
		justify-content: center;
		padding-left: 1em;
		/* transition: 0.3s; */
	}
	.button-container {
		position:fixed;
		z-index: 100;
	}

</style>

<svelte:head>
	<title>James Bradbury | Sound & Code</title>
</svelte:head>
<svelte:window bind:innerWidth={w} />

<div class="wrapper">
	{#if w < 1296}
	<div class="button-container">
		<button on:click={clickHandle}>Show Navigation</button>
	</div>
	{/if}
	{#if w > 1296}
	<StaticNav {segment}/>
	{:else if navshow}
	<StaticNav {segment}/>
	{/if}
	<main 
	class="content"
	>
		<slot></slot>
	</main>
</div>
