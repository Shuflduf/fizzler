<script lang="ts">
	import { onMount } from 'svelte';
	import Bottle from './Bottle.svelte';

	let count = $state(0);

	onMount(() => {
		count = 0;
		setInterval(spawn, 1000);
	});

	function spawn() {
		if (document.visibilityState == 'visible') {
			count++;
		}
	}
</script>

{#each Array(count)}
	<Bottle />
{/each}
