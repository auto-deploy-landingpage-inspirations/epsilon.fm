<script lang="ts">
	import { onMount, onDestroy } from 'svelte';
	import { sidebarVisible } from '$lib/stores/ui';
	import HomeCard from '@/components/HomeCard.svelte';
	import NewsletterCard from '$lib/components/NewsletterCard.svelte';
	import GitHubCorner from '$lib/components/GitHubCorner.svelte';

	let originalSidebarValue: boolean;

	onMount(() => {
		originalSidebarValue = $sidebarVisible;
		sidebarVisible.set(false);
	});

	onDestroy(() => {
		sidebarVisible.set(originalSidebarValue);
	});
</script>

<svelte:head>
	<title>Epsilon FM</title>
	<meta
		name="description"
		content="Our modern open-source music distribution platform includes a beautifully designed artist website, customised merch, generative AI music videos, and access to over one hundred global digital streaming platforms including Beatport, Traxsource, and Juno Download."
	/>
</svelte:head>

<GitHubCorner />
<div class="flex flex-grow flex-col items-center justify-center">
	<HomeCard></HomeCard>
	<NewsletterCard></NewsletterCard>
</div>
