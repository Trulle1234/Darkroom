<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';
	import { slide, } from "svelte/transition";

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
		["What is Darkroom?", 
			"Darkoom is a (prototype) Hack Club YSWS."],
		["What can i make?",
			"Anything related to photography! For example: an image editig app, a photo book website or your own camera app."],
		["Am I eligible to participate?", 
			"If you are between 13 and 18 your are eligible. You will have to verify your identity to purches stuff in the shop."],
		["So, what's the catch?",
			"There is none! Hack Club is a nonprofit who's goal is to help and encourage teens to make projects. I.e it's free witout any drawbacks."],
		["Can i use AI when making my project?",
			"We encourage you to do it on your own. But yes, you can use some AI (~30% max)."],
		["Who is running this?",
			"Darkroom is a part of Hack Club, a 501(c)(3) nonprofit organization. Darkroom is a prototype YSWS by Trulle123!"]
	];

	let openIndex: number | null = $state(null);

	function toggle(index: number) {
		if (openIndex === index) {
			openIndex = null;
		} else {
			openIndex = index;
			
		}
	}
</script>

<a href="https://hackclub.com/">
	<img
		src="https://cdn.hackclub.com/019cf26c-c031-7bb9-a8c4-216a5ecd5a28/flag-orpheus-left-color-fix.svg"
		alt="Hack Club"
		id="flag"
	/>
</a>

<div id="faq-button-div" class:visible={show}>
	<a href="#faq" id="faq-button">FAQ</a>
</div>

<div id="main" class:visible={show}>
	<div id="hero">
		<h1 id="title">Darkroom</h1>

		<p id="description">
			Build something photography related,<br>
			Get cameras, gear, film and other cool stuff!
		</p>
		
		<div id="buttons">
			<a href="https://trulle123.fillout.com/darkroom-rsvp" target="_blank" class="button">RSVP</a>
			<a href="https://hackclub.enterprise.slack.com/archives/C0ALM44RBFU" target="_blank" class="button">Join #darkroom</a>
		</div>
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
					<button class="question" onclick={() => toggle(i)}>
					<span>{q}</span>
					<span class:open={openIndex === i} class="arrow">▼</span>
					</button>
					
					{#if openIndex === i}
					<div class="answer"  transition:slide={{ duration: 280 }}>
						{a}
					</div>
					{/if}
				</div>			
  			{/each}
		</div>
		
		<p id="made-by">Made with ❤︎⁠ by 
		<a href="https://hackclub.enterprise.slack.com/team/U07904YUJ6A" target="_blank">Trulle123</a>
		& <a href="https://hackclub.com/" target="_blank">Hack Club</a></p>
	</div>
</div>