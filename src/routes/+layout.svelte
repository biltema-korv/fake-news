<script>
	import favicon from '$lib/assets/favicon.svg';
	import { base } from '$app/paths';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<a href="{base}/">Home</a>
	<a href="{base}/aboutus">About Us</a>
</svelte:head>

{@render children()}
