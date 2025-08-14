<script lang="ts">
	let { question, answer }: { question: string; answer: string } = $props();
</script>

<div class="h-32 rounded-lg border-4 border-[#B97375] bg-[#CEB1BE] p-4">
	<b>{question}</b>
	<p>{answer}</p>
</div>
