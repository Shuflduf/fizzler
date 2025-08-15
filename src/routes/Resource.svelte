<script lang="ts">
	let {
		children,
		name,
		imgPath,
		link,
		flipped
	}: { children: any; name: string; imgPath: string; link: string; flipped: boolean } = $props();
</script>

<div
	class="mx-auto flex w-5xl items-center justify-between gap-8 {flipped
		? 'flex-row-reverse'
		: 'flex-row'}"
>
	<a href={link} class="group text-center font-[Arvo] text-2xl font-bold text-nowrap">
		<img src={imgPath} alt="tauri" class="asp mx-auto mb-4 h-24 transition group-hover:scale-105" />
		<p>{name}</p>
	</a>
	<div class="h-48 min-w-1 rounded-full bg-[#9DF7E5] mask-y-from-80% mask-y-to-100%"></div>
	<p class="text-xl font-bold {flipped ? 'text-right' : 'text-left'}">
		{@render children()}
	</p>
</div>
