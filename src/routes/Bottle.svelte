<script lang="ts">
	import { onMount } from 'svelte';

	const DELTA = 60 / 1000;
	const MAX_SPEED = 20.0;
	const IMAGE_PATHS = ['fizzies/pepsi.png', 'fizzies/monster.png', 'fizzies/lemonade.png'];

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
		length(): number {
			return Math.sqrt(this.x ** 2 + this.y ** 2);
		}
	}

	function lerp(a: number, b: number, t: number): number {
		return a + (b - a) * t;
	}

	let mousePos: Vec2 = new Vec2(0, 0);
	let mouseVel: Vec2 = new Vec2(0, 0);

	let imgIndex = $state(0);
	let held = $state(false);
	let pageHeight = $state(10000);
	let pos: Vec2 = $state(new Vec2(0, -100));
	let vel: Vec2 = $state(new Vec2(0, MAX_SPEED));
	let rot: number = $state(0);

	onMount(() => {
		setInterval(process, DELTA);

		const leftSide = Math.random() > 0.5;
		if (leftSide) {
			pos = new Vec2(lerp(0, 200, Math.random()), pos.y);
		} else {
			const rightEdge = window.innerWidth - 96;
			pos = new Vec2(lerp(rightEdge, rightEdge - 200, Math.random()), pos.y);
		}

		vel = new Vec2(lerp(-2, 2, Math.random()), vel.y);
		rot = lerp(0, 360, Math.random());

		imgIndex = Math.floor(Math.random() * IMAGE_PATHS.length);
		pageHeight = document.body.scrollHeight;
		window.addEventListener('mousemove', (e: MouseEvent) => {
			const newPos = new Vec2(e.clientX + window.scrollX, e.clientY + window.scrollY);
			mouseVel = newPos.minus(mousePos);
			mousePos = newPos;
		});
		window.addEventListener('mouseup', (_) => {
			if (held) {
				document.body.style.userSelect = 'auto';
				held = false;
				vel = mouseVel.scale(0.5 / DELTA);
			}
		});
	});

	function process() {
		// pos.add(vel);
		vel = vel.plus(new Vec2(0.0, 10 * DELTA));
		if (vel.y > MAX_SPEED) {
			vel = vel.lerp(new Vec2(vel.x, MAX_SPEED), DELTA);
		}

		if (pos.x < 0) {
			vel.x = Math.abs(vel.x * 0.3);
			pos.x = 0;
		}
		if (pos.x > window.innerWidth - 96) {
			vel.x = -Math.abs(vel.x * 0.3);
			pos.x = window.innerWidth - 96;
		}

		pos = pos.plus(vel.scale(DELTA));
		rot += vel.x * DELTA;

		if (held) {
			console.log(mousePos);
			pos = mousePos.plus(new Vec2(-48, -48));
			vel = new Vec2(0, 0);
		}
	}

	function mouseDown(_: MouseEvent) {
		held = true;
		document.body.style.userSelect = 'none';
	}
</script>

{#if pos.y < pageHeight - 96}
	<div
		role="button"
		tabindex="-1"
		style="top: {pos.y}px; left: {pos.x}px; cursor: {held ? 'grabbing' : 'grab'}; rotate: {rot}deg"
		class="absolute z-50 size-24"
		onmousedown={mouseDown}
	>
		<img src={IMAGE_PATHS[imgIndex]} class="pointer-events-none select-none" alt="bottle" />
	</div>
{/if}
