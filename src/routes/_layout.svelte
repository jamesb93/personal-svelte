<!-- https://daveceddia.com/svelte-with-sass-in-vscode/ -->
<!-- https://stackoverflow.com/questions/32378953/keep-the-middle-item-centered-when-side-items-have-different-widths -->
<!-- https://css-tricks.com/full-bleed/ -->

<script>
	import StaticNav from "../components/StaticNav.svelte"
	export let segment;
	let w;
	let navshow = false;

	function clickHandle() {
		navshow = !navshow;
	}
	$: if (w < 1296) {navshow = false};
	const backgroundClickHandle=()=>{navshow = false};
</script>

<style>
	/* Grid */
	.wrapper {
		display: grid;
		grid-template-columns: auto min(83ch, 100%) auto;
		justify-content: center;
		padding-left: 0em;
		padding-right: 0em;
		max-width: 150ch;
		margin: 0 auto;
	}

	.wrapper > * {
		grid-column: 2;
	}

	.content {
		margin-top: 5em;
		justify-content: center;
		padding-left: 1em;
		height: 100%;
	}

	.dim {
		opacity: 0.25;
	}

	svg {
		min-height: 24px;
		transition: transform 0.3s ease-in-out;
	}
	
	svg line {
		stroke: darkgray;
		stroke-width: 2;
		transition: transform 0.3s ease-in-out
	}

	.btn {
		background-color: white;
		box-shadow: none;
		border-width: 0px;
	}

	.btn-container {
		position:fixed;
		z-index: 100;
	}
</style>

<svelte:head>
	<title>James Bradbury | Sound & Code</title>
</svelte:head>
<svelte:window bind:innerWidth={w} />
<main class="wrapper">
	{#if w < 1296}
		<div class="btn-container">
			<button on:click={clickHandle} class="btn">
				<!-- nav -->
				<svg width=24 height=20>
					<line x1=0 y1=4  x2=24 y2=4/>
					<line x1=0 y1=11  x2=16 y2=11/>
					<line x1=0 y1=18 x2=24  y2=18/>
				</svg>
			</button>
		</div>
	{/if}
	{#if w > 1296 || navshow}
		<StaticNav {segment} bind:navshow={navshow}/>
	{/if}
	<article
	on:click={backgroundClickHandle} 
	class="content" 
	class:dim='{w < 1296 && navshow}'
	><slot></slot>
	<br>
	</article>
</main>
