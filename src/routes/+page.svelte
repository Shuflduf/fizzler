<script>
	import SlackLink from '$lib/SlackLink.svelte';
	import Question from './Question.svelte';
</script>

<div class="h-[35rem] w-full bg-[#CEB1BE]">
	<div class="mx-auto flex h-full w-7xl flex-row items-center">
		<div class="flex h-full w-full flex-col items-center justify-center">
			<h1 class="font-[Arvo] text-9xl font-bold text-[#2D2D34]">Fizzler</h1>
			<h2 class="font-[Arvo] text-4xl text-[#2D2D34]">Make a Tauri app, Get a Fizzy Drink!</h2>
		</div>
		<div class="h-full w-full">some image would go here maybe</div>
	</div>
</div>
<div class="h-1 w-full bg-[#B97375]"></div>
<div class="flex h-[35rem] w-full flex-col justify-center bg-[#E2DCDE]">
	<div class="mx-auto w-[60rem]">
		<h1 class="mb-8 text-center font-[Arvo] text-7xl font-bold">Instructions</h1>
		<ul class="flex list-disc flex-col gap-4 text-2xl">
			<li>
				<b>Come up with an idea:</b> Your Tauri app could be anything from a music player to a desktop
				pet! Be creative!
			</li>
			<li>
				<b>Make it using Tauri:</b> This requires experience with front-end development with any framework,
				and Rust for backend development.
			</li>
			<li>
				<b>Submit your project to earn a <i>Fizzy Drink</i>:</b> Minimum 5 hours, tracked with Hackatime.
			</li>
			<li>
				<b>
					Show off your drink in
					<SlackLink link="https://hackclub.slack.com/archives/C09AD0R1SUV">#fizzlers</SlackLink>:
				</b> Pepsi, Monster, some obscure energy drink, pretty much anything that you SHOULDN'T shake
				before opening!
			</li>
		</ul>
	</div>
</div>
<div class="h-1 w-full bg-[#B97375]"></div>

<div class="flex h-[40rem] w-full flex-col justify-center bg-[#F1E4E8]">
	<div class="mx-auto flex h-full w-4xl flex-col justify-center gap-8">
		<h1>FAQ</h1>
		<div class="flex w-full flex-row justify-center gap-8">
			<Question
				question="Can I submit an existing project?"
				answer="You need to create a new project for Fizzler, existing projects won't be accepted."
			/>
			<Question question="Can I submit my project for Summer of Making as well?" answer="🐸🚀" />
		</div>
	</div>
</div>
