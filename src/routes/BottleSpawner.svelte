<script lang="ts">
	import { onMount } from 'svelte';
	import Bottle from './Bottle.svelte';

	let isMobile = $state(false);
	let count = $state(0);
	let disabled = $state(false);

	onMount(() => {
		count = 0;
		setInterval(spawn, 1000);
		window.addEventListener('resize', (e: UIEvent) => {
			isMobile = window.innerWidth < 768;
		});
		isMobile = window.innerWidth < 768;
	});

	function spawn() {
		if (disabled || isMobile) {
			count = 0;
			return;
		}
		if (document.visibilityState == 'visible') {
			count++;
		}
		// 	count = 0;
		// }
	}
</script>

{#each Array(count)}
	<Bottle />
{/each}

<div class="absolute top-4 left-1/2 z-50 hidden -translate-x-1/2 flex-row gap-4 md:flex">
	<p class="font-[Arvo] text-2xl font-bold text-white">Disable Fizzies</p>
	<input type="checkbox" bind:checked={disabled} />
</div>
