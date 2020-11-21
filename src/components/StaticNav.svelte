<script>
	import { fly } from 'svelte/transition';
	export let segment;
	export let navshow;
	const handleClick = () => {navshow = false};
</script>

<nav
transition:fly="{{duration: 230, x: -50}}"
class="container"
>
	<ul>
		<br>
		<li><a class="name" rel=prefetch class:selected='{segment === undefined}' href='.'>James Bradbury</a></li>
		<i>james.bradbury@hud.ac.uk</i>

		<br><br>
		<span class="name">info</span>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "music"}'  		href='music'>music</a></li>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "media"}'  		href='media'>media</a></li>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "performances"}'   href='performances'>performances</a></li>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "code"}'  			href='code'>code</a></li>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "publications"}'   href='publications'>publications</a></li>
		<br>
		<span class="name">projects</span>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "reacoma"}'   				href='reacoma'>ReaCoMa</a></li>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "annealing-strategies"}'   href='annealing-strategies'>annealing strategies</a></li>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "biomimicry"}'   			href='biomimicry'>biomimicry</a></li>
		<br>
		<span class="name">links</span>
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "creative-coding"}' href='creative-coding'>creative coding/consulting</a></li>
		<!-- <li><a rel=prefetch on:click={handleClick} class:selected='{segment === "people"}' href='people'>people</a></li> -->
		<li><a rel=prefetch on:click={handleClick} class:selected='{segment === "tech"}'   			href='tech'>tech/honourable mentions</a></li>
		<li><a target="blank" on:click={handleClick} href="https://www.github.com/jamesb93">Github</a></li>
		<li><a class="hidden" href='reconstruction_error'>reconstruction error</a></li>
	</ul>
</nav>


<style>
	.name {color:rgb(0, 0, 0)}
	.hidden {color: white;}
	.hidden:hover {color: white;}
	.container {
		position: fixed;
		height: 100%;
		background-color: white;
		z-index: 99;
		box-shadow: 1em;
		padding-left: 1em;
	}

	nav {
		min-width: max-content;
		max-width: max-content;
		padding-left: 0;
		transition: 0.1s;
		height: 100%;
		padding-right: 0.5em;
		z-index: 200;
	}
	ul {
		font-size: 12px;
		color: rgb(127, 127, 127);
		word-wrap: none;
		padding-left: 0;
		opacity: 1;
		padding-top: 5em;
	}

	ul li {
		display: block;
		padding-left: 0;
	}

	ul li a {
		text-decoration: none;
		/* padding: 0.1em; */
		display: block;
	}
	
	ul li a:hover {
		color: rgb(95, 95, 95)
	}
	
	a {
		color: rgb(127, 127, 127)
	}
	
	a:hover {
		color: rgb(178, 178, 178)
	}

	.selected {
		display: inline-block;
		color: rgb(0, 0, 0)
	}
</style>
