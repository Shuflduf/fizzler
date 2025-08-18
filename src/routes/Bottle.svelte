<script lang="ts">
	import { onMount } from 'svelte';

	const DELTA = 1000 / 60;
	const MAX_FALL = 0.5;

	class Vec2 {
		x: number;
		y: number;

		constructor(x: number, y: number) {
			this.x = x;
			this.y = y;
		}

		plus(other: Vec2): Vec2 {
			const newVec = new Vec2(this.x, this.y);
			newVec.x += other.x;
			newVec.y += other.y;
			return newVec;
		}
		times(other: Vec2): Vec2 {
			return new Vec2(this.x * other.x, this.y * other.y);
		}
		scale(scalar: number): Vec2 {
			return new Vec2(this.x * scalar, this.y * scalar);
		}
	}

	let pageHeight = $state(10000);

	let pos: Vec2 = $state(new Vec2(0, 0));
	let vel: Vec2 = $state(new Vec2(0, 0));

	onMount(() => {
		setInterval(process, DELTA);

		pageHeight = document.body.scrollHeight;
	});

	function process() {
		// pos.add(vel);
		vel = vel.plus(new Vec2(0.0, 0.01));
		if (vel.y > MAX_FALL) {
			vel = new Vec2(vel.x, MAX_FALL);
		}

		pos = pos.plus(vel.scale(DELTA));
	}
</script>

{#if pos.y < pageHeight}
	<div style="top: {pos.y}px; left: {pos.x}px;" class="absolute z-50 size-12 bg-red-500">A</div>
{/if}
