<script lang="ts">
	let { children, question }: { children: any; question: string } = $props();
</script>

<div class="w-full max-w-md text-center text-lg text-[#AF4D98]">
	<b>{question}</b>
	{@render children()}
</div>
