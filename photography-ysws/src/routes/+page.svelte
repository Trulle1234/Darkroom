<script lang="ts">
	import '../app.css';
    import { onMount } from 'svelte';
    import { blur, crossfade, draw, fade, fly, scale, slide } from 'svelte/transition';

	let show = $state(false);

	onMount(() => {
		show = true;
        console.log("loaded");
	});
</script>

<a href="https://hackclub.com/">
	<img
		src="/images/flag-orpheus-left-color-fix.svg"
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
                Get Cameras, Gear, film and other cool stuff!
            </p>
        </div>
    </div>
{/if}