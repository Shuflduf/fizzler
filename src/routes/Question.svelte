<script lang="ts">
	let { children, question }: { children: any; question: string } = $props();
</script>

<div class="w-md text-lg text-[#AF4D98]">
	<b>{question}</b>
	{@render children()}
</div>
