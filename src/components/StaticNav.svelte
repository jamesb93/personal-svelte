<script>
	export let segment;
	import { fade } from 'svelte/transition';
</script>

<style>
	nav {
		min-width: max-content;
		max-width: max-content;
		padding-left: 0;
		transition: 0.1s;
		height: 100%;
		padding-right: 1em;
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
	}

	.selected {
		display: inline-block;
		color: rgb(0, 0, 0)
	}

	
	ul li a {
		text-decoration: none;
		padding: 0.1em;
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

	.delim {
		color:black;
	}

	.container {
		position: fixed;
		height: 100%;
		background-color: white;
		z-index: 99;
	}
</style>

<div transition:fade class="container" id="nav-container">
	<nav transition:fade id="nav">
		<ul transition:fade>
			<br>
			<li><a rel=prefetch class:selected='{segment === undefined}'  		href='.'>James Bradbury</a></li>
			<i>james.bradbury@hud.ac.uk</i>
	
			<br><br>
			<span class="delim">info</span>
			<li><a rel=prefetch class:selected='{segment === "music"}'  		href='music'>music</a></li>
			<li><a rel=prefetch class:selected='{segment === "media"}'  		href='media'>media</a></li>
			<li><a rel=prefetch class:selected='{segment === "performances"}'   href='performances'>performances</a></li>
			<li><a rel=prefetch class:selected='{segment === "code"}'  			href='code'>code</a></li>
			<li><a rel=prefetch class:selected='{segment === "publications"}'   href='publications'>publications</a></li>
			<br>
			<span class="delim">projects</span>
			<li><a rel=prefetch class:selected='{segment === "reacoma"}'   				href='reacoma'>ReaCoMa</a></li>
			<li><a rel=prefetch class:selected='{segment === "annealing-strategies"}'   href='annealing-strategies'>annealing strategies</a></li>
			<li><a rel=prefetch class:selected='{segment === "biomimicry"}'   			href='biomimicry'>biomimicry</a></li>
			<br>
			<span class="delim">links</span>
			<li><a target="blank" href="https://www.github.com/jamesb93">Github</a></li>
			<li><a rel=prefetch class:selected='{segment === "tech"}'   			href='tech'>tech/honourable mentions</a></li>
		</ul>
	</nav>
</div>

