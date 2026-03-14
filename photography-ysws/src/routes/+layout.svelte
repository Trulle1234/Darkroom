<script lang="ts">
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="https://icons.hackclub.com/api/icons/0xe6e1da/camera-fill"/>
</svelte:head>

{@render children()}