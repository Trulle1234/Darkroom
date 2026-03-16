<script lang="ts">
	export const prerender = true;
	let { children } = $props();
</script>

<svelte:head>
	<title>Darkroom</title>
	<link rel="icon" href="https://icons.hackclub.com/api/icons/0xe6e1da/camera-fill"/>
</svelte:head>

{@render children()}