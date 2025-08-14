<script lang="ts">
	let { children, link }: { link: string; children: any } = $props();
</script>

<a
	href={link}
	class="rounded-md bg-[#e1edf2] px-1 font-normal text-[#1164a2] transition duration-[50] hover:bg-[#cbe3ee] hover:text-[#0c4c8c]"
>
	{@render children()}
</a>
