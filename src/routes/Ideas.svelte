<script lang="ts">
	import { onMount } from 'svelte';

	const DELTA: number = 1000 / 60;

	let list: HTMLDivElement;
	let currentIdeas: any[] = $state([1, 2, 3, 4, 5]);

	onMount(() => {
		setInterval(scrollList, DELTA);
	});

	function scrollList() {
		list.scrollBy({ left: DELTA / 5 });
	}

	function onListScroll(e: Event) {
		console.log(e);
		const target = e.target as HTMLDivElement;
		const shouldSpawn = target.scrollLeft + target.clientWidth + 80 > target.scrollWidth;
		if (shouldSpawn) {
			currentIdeas.push(2);
		}
	}
</script>

<div
	class="flex max-w-[100vw] flex-row gap-4 overflow-x-auto mask-x-from-80% mask-x-to-95%"
	bind:this={list}
	onscroll={onListScroll}
>
	{#each currentIdeas}
		<div class="h-60 min-w-lg bg-red-500"></div>
	{/each}
</div>
