<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';

	let show = $state(false);

	onMount(() => {
		show = true;
	});

	let items = [
		["https://cdn.hackclub.com/019cf3a4-5c6d-7085-ae8c-b6e7267c1257/instax_crop.png",
			"Instax", "An Instax camera"],
		["https://cdn.hackclub.com/019cf3a4-5e21-7fcf-a9e9-cd2ad4f39e76/memory_cards_crop.png", 
			"Memory cards", "Memory cards to store your photos"],
		["https://cdn.hackclub.com/019cf3a4-6360-7cfe-abcc-f1248cd352a7/printed_photps_crop.png",
			"Printed Photos", "A grant to print your photos"],
		["https://user-cdn.hackclub-assets.com/019cf3ab-4853-70fe-b981-c9e504397c82/kodak_chamera_crop.png",
			"Kodak Charmera", "Kodak Charmera - A keychain camera"],
		// not done below here
		["https://cdn.hackclub.com/019cf3c0-970b-7f23-8cc8-29eb8d212ea1/placeholder.png",
			"Placeholder", "Placeholder"],
		["https://cdn.hackclub.com/019cf3c0-970b-7f23-8cc8-29eb8d212ea1/placeholder.png",
			"Placeholder", "Placeholder"],
		["https://cdn.hackclub.com/019cf3c0-970b-7f23-8cc8-29eb8d212ea1/placeholder.png",
			"Placeholder", "Placeholder"],
		["https://cdn.hackclub.com/019cf3c0-970b-7f23-8cc8-29eb8d212ea1/placeholder.png",
			"Placeholder", "Placeholder"],
	];
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
			Build something photography related,<br>
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
			{#each items as [url, alt, desc]}
				<div class="polaroid-wrap" style="transform: rotate(
					{Math.random() < 0.4
						? -(Math.random() * 5 + 5)
						: Math.random() * 5 + 5}deg);">
						
					<img
						src={url}
						alt={alt}
						class="polaroid-img"
					/>
					<img
						src="https://cdn.hackclub.com/019cf277-b514-7a8f-96f5-c33a5dc49504/polaroid.svg"
						alt="Polaroid"
						class="polaroid"
					/>
					<p class="polaroid-text">{desc}</p>
				</div>
			{/each}
		</div>
	</div>
</div>