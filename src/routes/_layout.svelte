<!-- https://daveceddia.com/svelte-with-sass-in-vscode/ -->
<!-- https://stackoverflow.com/questions/32378953/keep-the-middle-item-centered-when-side-items-have-different-widths -->
<!-- https://css-tricks.com/full-bleed/ -->

<script>
	import StaticNav from "../components/StaticNav.svelte"
	export let segment;
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

	.wrapper > * {
		grid-column: 2;
	}

	.content {
		margin-top: 5em;
		justify-content: center;
		padding-left: 1em;
	}

</style>

<svelte:head>
	<title>James Bradbur | Sound & Code</title>
</svelte:head>

<div class="wrapper">
	<StaticNav {segment} />
	<main class="content"><slot></slot></main>
</div>
