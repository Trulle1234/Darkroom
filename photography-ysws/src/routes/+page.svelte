<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';

	let show = $state(false);

	onMount(() => {
		show = true;
	});
</script>

<a href="https://hackclub.com/">
	<img
		src="https://cdn.hackclub.com/019cf26c-c031-7bb9-a8c4-216a5ecd5a28/flag-orpheus-left-color-fix.svg"
		alt="Hack Club"
		id="flag"
	/>
</a>

<div id="main" class:visible={show}>
	<div id="hero">
		<h1 id="title">Darkroom</h1>

		<p id="description">
			Build something photography related<br>
			Get cameras, gear, film and other cool stuff!
		</p>
	</div>
</div>

<img 
	src="https://cdn.hackclub.com/019cf2b0-6906-7246-8451-490d4e152f0d/wave.svg"
	alt="Wave"
	id="wave"
/>

<div id="dark">
	<div class:visible={show}>
		<h6 id="get">Get stuff like:</h6>
		<i id="det-disclaimer">*This is subject to change!</i>
		
		<div id="polaroid-grid">
			{#each Array(8) as _, i}
				<img 
					src="https://cdn.hackclub.com/019cf277-b514-7a8f-96f5-c33a5dc49504/polaroid.svg"
					alt="Polaroid"
					class="polaroid"
				/>
			{/each}
		</div>
	</div>
</div>