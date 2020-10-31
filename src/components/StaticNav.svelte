<script>
	export let segment;
</script>

<style>
	ul {
		font-size: 12px;
		margin-top: 7em;
		min-width: max-content;
		max-width: max-content;
		color: rgb(127, 127, 127);
		word-wrap: none;
		padding-left: 0;
		position: fixed;
		margin-left: 5em;
	}

	ul li {
		flex: 1;
		display: block;
	}

	.selected {
		position: relative;
		display: inline-block;
		color: rgb(0, 0, 0)
	}

	.project {
		margin-left: 1em;
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
	
    @media only screen and (max-width: 1296px) {
		ul {display: none}
	}

	.delim {
		color:black;
	}
</style>
<ul>
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
