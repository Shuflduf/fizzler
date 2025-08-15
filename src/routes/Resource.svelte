<script lang="ts">
	let {
		children,
		name,
		imgPath,
		flipped
	}: { children: any; name: string; imgPath: string; flipped: boolean } = $props();
</script>

<div
	class="mx-auto flex w-3xl items-center justify-between gap-8 {flipped
		? 'flex-row-reverse'
		: 'flex-row'}"
>
	<a
		href="https://v2.tauri.app/start/"
		class="group text-center font-[Arvo] text-2xl font-bold text-nowrap"
	>
		<img src={imgPath} alt="tauri" class="mx-auto mb-4 h-24 transition group-hover:scale-105" />
		<p>{name}</p>
	</a>
	<div class="h-48 w-2 rounded-full bg-[#9DF7E5] mask-y-from-80% mask-y-to-100%"></div>
	<p class="text-lg font-bold">
		{@render children()}
	</p>
</div>
