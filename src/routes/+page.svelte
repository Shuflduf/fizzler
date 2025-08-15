<script>
	import FizzlerSlackLink from '$lib/FizzlerSlackLink.svelte';
	import Question from './Question.svelte';
</script>

<div class="h-[35rem] w-full bg-[#AF4D98]">
	<div class="mx-auto flex h-full w-7xl flex-row items-center">
		<div class="flex h-full w-full flex-col items-center justify-center">
			<h1 class="font-[Arvo] text-9xl font-bold text-[#F4E4BA]">Fizzler</h1>
			<h2 class="font-[Arvo] text-4xl text-[#F4E4BA]">Make a Tauri app, Get a Fizzy Drink!</h2>
		</div>
		<div class="h-full w-full">some image would go here maybe</div>
	</div>
</div>

<div class="flex h-[35rem] w-full flex-col justify-center bg-[#D66BA0] text-[#9DF7E5]">
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
				<b>Submit your project to earn a <i>Fizzy Drink</i>:</b> 5$ USD per hour spent on project,
				maximum 5 hours. Tracked with
				<a class="text-blue-500 hover:text-blue-400" href="https://hackatime.hackclub.com/"
					>Hackatime</a
				>
			</li>
			<li>
				<b>
					Show off your drink in <FizzlerSlackLink />:
				</b> Pepsi, Monster, some obscure energy drink, pretty much anything that you SHOULDN'T shake
				before opening!
			</li>
		</ul>
	</div>
</div>

{#snippet questionSpacer()}
	<div
		class="mx-auto my-4 h-1 w-2xl rounded-full bg-[#AF4D98] mask-radial-from-0 mask-radial-to-80% mask-radial-at-center"
	></div>
{/snippet}

<div class="flex h-[40rem] w-full flex-col justify-center bg-[#9DF7E5] text-[#AF4D98]">
	<h1 class="mb-8 text-center font-[Arvo] text-7xl font-bold">FAQ</h1>
	<div class="flex w-full flex-row justify-center gap-8">
		<Question question="Can I submit an existing project?">
			<p>You need to create a new project for Fizzler, existing projects won't be accepted.</p>
		</Question>
		<Question question="Can I submit my project for Summer of Making as well?">
			<p>Unfortunately, no...</p>
		</Question>
	</div>
	{@render questionSpacer()}
	<div class="flex w-full flex-row justify-center gap-8">
		<Question question="Is AI allowed?">
			<p>
				We advise against it, since it removes the fun of making it yourself, but if you do use it,
				you need to say so on your submission form.
			</p>
		</Question>
		<Question question="What platforms do I make my app for?">
			<p>
				If you're making a desktop app, then Windows, MacOS, and Linux. If you're making a mobile
				app, then just Android. (IF IOS THEN REACH OUT TO US ON SLACK (<FizzlerSlackLink />))
			</p>
		</Question>
	</div>
	{@render questionSpacer()}
	<div class="flex w-full flex-row justify-center gap-8">
		<Question question="Where can I learn Tauri?">
			<p>
				The <a href="https://v2.tauri.app/start/" class="text-blue-500 hover:text-blue-400">
					Tauri docs
				</a>
				provide a guide for creating a basic project, and you can look at
				<a
					href="https://github.com/Shuflduf/Tauri-Game-Launcher"
					class="text-blue-500 hover:text-blue-400"
				>
					the example project
				</a> for a complete example.
			</p>
		</Question>
		<Question question="How do I host my app?">
			<p>
				<a
					class="text-blue-500 hover:text-blue-400"
					href="https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository"
				>
					Github releases.
				</a>
			</p>
		</Question>
	</div>
</div>

<div class="flex h-[40rem] w-full flex-col justify-center bg-[#F4E4BA] text-[#D66BA0]">
	<h1 class="mb-8 text-center font-[Arvo] text-7xl font-bold">Some Ideas</h1>
</div>
