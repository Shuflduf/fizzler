<script lang="ts">
	import { onMount } from 'svelte';

	const DELTA: number = 1000 / 60;

	let allIdeas: string[];
	let list: HTMLDivElement;
	let currentIdeas: string[] = $state([]);
	let currentIndex: number = 0;

	onMount(async () => {
		allIdeas = await (await fetch('ideas.json')).json();
		currentIdeas = allIdeas;
		setInterval(scrollList, DELTA);
	});

	function scrollList() {
		if (list) {
			list.scrollBy({ left: DELTA / 10 });
		}
	}

	function onListScroll(e: Event) {
		const target = e.target as HTMLDivElement;
		const shouldSpawn = target.scrollLeft + target.clientWidth + 80 > target.scrollWidth;
		if (shouldSpawn) {
			console.log('spawning');
			currentIndex++;
			if (currentIndex >= allIdeas.length) {
				currentIndex = 0;
			}
			currentIdeas.push(allIdeas[currentIndex]);
		}
	}
</script>

<div
	class="no-scrollbar flex max-w-[100vw] flex-row gap-4 overflow-x-auto mask-x-from-80% mask-x-to-95%"
	bind:this={list}
	onscroll={onListScroll}
>
	{#each currentIdeas as idea}
		<div class="px-4 text-lg text-nowrap">{idea}</div>
	{/each}
</div>
