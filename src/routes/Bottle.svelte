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
		minus(other: Vec2): Vec2 {
			return new Vec2(this.x - other.x, this.y - other.y);
		}
		times(other: Vec2): Vec2 {
			return new Vec2(this.x * other.x, this.y * other.y);
		}
		scale(scalar: number): Vec2 {
			return new Vec2(this.x * scalar, this.y * scalar);
		}
		lerp(other: Vec2, t: number): Vec2 {
			return new Vec2(lerp(this.x, other.x, t), lerp(this.y, other.y, t));
		}
	}

	function lerp(a: number, b: number, t: number): number {
		return a + (b - a) * t;
	}

	let mousePos: Vec2 = new Vec2(0, 0);
	let mouseVel: Vec2 = new Vec2(0, 0);
	let held = false;

	let pageHeight = $state(10000);
	let pos: Vec2 = $state(new Vec2(0, 0));
	let vel: Vec2 = $state(new Vec2(0, 0));

	onMount(() => {
		setInterval(process, DELTA);

		pageHeight = document.body.scrollHeight;
		window.addEventListener('mousemove', (e: MouseEvent) => {
			const newPos = new Vec2(e.clientX + window.scrollX, e.clientY + window.scrollY);
			mouseVel = newPos.minus(mousePos);
			mousePos = newPos;
		});
		window.addEventListener('mouseup', (_) => {
			if (held) {
				held = false;
				vel = mouseVel.scale(0.05);
			}
		});
	});

	function process() {
		// pos.add(vel);
		vel = vel.plus(new Vec2(0.0, 0.01));
		if (vel.y > MAX_FALL) {
			vel = vel.lerp(new Vec2(vel.x, MAX_FALL), DELTA);
		}

		pos = pos.plus(vel.scale(DELTA));

		if (held) {
			console.log(mousePos);
			pos = mousePos.plus(new Vec2(-48, -48));
		}
	}
</script>

{#if pos.y < pageHeight}
	<div
		role="button"
		tabindex="-1"
		style="top: {pos.y}px; left: {pos.x}px;"
		class="absolute z-50 size-24 bg-red-500"
		onmousedown={() => (held = true)}
	></div>
{/if}
