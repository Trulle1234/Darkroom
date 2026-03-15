<script lang="ts">
	import '../app.css';
    import { onMount } from 'svelte';
    import { blur } from 'svelte/transition';

	let show = $state(false);

	onMount(() => {
		show = true;
        console.log("loaded");
	});
</script>

<a href="https://hackclub.com/">
	<img
		src="https://cdn.hackclub.com/019cf26c-c031-7bb9-a8c4-216a5ecd5a28/flag-orpheus-left-color-fix.svg"
		alt="Hack Club"
		id="flag"
	/>
</a>


{#if show}
    <div id="main" transition:blur={{ duration: 1000 }}>
        <div id="hero">
            <h1 id="title">Darkroom</h1>

            <p id="description">
                Build something photography related<br>
                Get cameras, gear, film and other cool stuff!
            </p>
        </div>
    </div>
{/if}


<img 
    src="https://cdn.hackclub.com/019cf2b0-6906-7246-8451-490d4e152f0d/wave.svg"
    alt="Wave"
    id="wave"
/>

<div id="dark">
    <h6 id="get">Get stuff like:</h6>
    
    <div id="polaroid-grid">
        {#each { length: 6 }}
            <img 
                src="https://cdn.hackclub.com/019cf277-b514-7a8f-96f5-c33a5dc49504/polaroid.svg"
                alt="Polaroid"
                class="polaroid"
                id="polaroid-1"
            />
        {/each}
    </div>
</div>