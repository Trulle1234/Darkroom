<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';

	let show = $state(false);

	onMount(() => {
		show = true;
	});

	let items = [
		["https://cdn.hackclub.com/019cf3a4-5c6d-7085-ae8c-b6e7267c1257/instax_crop.png",
			"Instax", "An Instax instant camera"],
		["https://cdn.hackclub.com/019cf3a4-5e21-7fcf-a9e9-cd2ad4f39e76/memory_cards_crop.png", 
			"Memory cards", "Memory cards to store your photos"],
		["https://cdn.hackclub.com/019cf658-bc26-752a-8278-4eabf833026d/accessories_crop.png",
			"Accessories", "A grant for accessories"],
		["https://user-cdn.hackclub-assets.com/019cf3ab-4853-70fe-b981-c9e504397c82/kodak_chamera_crop.png",
			"Kodak Charmera", "Kodak Charmera - A keychain camera"],
		["https://cdn.hackclub.com/019cf63c-c237-7edf-bedb-aa6554c0fdd9/sticker_sheet_placeholder_crop.png",
			"Sticker sheet", "A cool sticker sheet!"],
		["https://cdn.hackclub.com/019cf63c-be51-7b67-aa1b-aa18b0012a12/film_crop.png",
			"Film", "Some Instax film, possibly others too"],
		["https://cdn.hackclub.com/019cf63c-c06e-77ce-90d8-ad3a0f4e9750/digicam_crop.png",
			"Digicam", "A Digicam, exactly which is tbd"],
		["https://cdn.hackclub.com/019cf3a4-6360-7cfe-abcc-f1248cd352a7/printed_photps_crop.png",
			"Printed Photos", "A grant to get your photo printed"],
		];

	let faqs = [
		["Am I eligible to participate?", "If you are between 13 and 18 your are eligible. You will have to verify your identity to purches stuff in the shop."],
		["Question", "Answer"],
	];

	let openIndex: number | null = $state(null);

	function toggle(index: number) {
		openIndex = openIndex === index ? null : index;
	}
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
		<h2 id="get">Get stuff like:</h2>
		<i id="det-disclaimer">*This is subject to change!</i>

		<div id="polaroid-grid">
			{#each items as [url, alt, desc]}
				<div class="polaroid-wrap" style="transform: rotate(
					{Math.random() < 0.5
						? -(Math.random() * 4 + 2)
						: Math.random() * 4 + 2}deg);">
						
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
		
		<h2 id="faq-head">FAQ:</h2>

		<div id="faq">
			{#each faqs as [q, a], i}
				<div class="faq-item">
					<button onclick={() => toggle(i)}>
					{q}
					<span>{openIndex === i ? '▲' : '▼'}</span>
					</button>
					
					{#if openIndex === i}
					<div class="answer">
						{a}
					</div>
					{/if}
				</div>			
  			{/each}
		</div>
	</div>
</div>