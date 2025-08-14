<script lang="ts">
	let { children, question }: { children: any; question: string } = $props();
</script>

<div class="w-md rounded-lg border-2 border-[#B97375] bg-[#CEB1BE] p-4">
	<b>{question}</b>
	{@render children()}
</div>
