<script>
	import FizzlerSlackLink from '$lib/FizzlerSlackLink.svelte';
	import SlackLink from '$lib/SlackLink.svelte';
	import BottleSpawner from './BottleSpawner.svelte';
	import Ideas from './Ideas.svelte';
	import Question from './Question.svelte';
	import Resource from './Resource.svelte';
</script>

<BottleSpawner />

<!-- TODO: make this look better on mobile -->
<div class="h-[70vh] w-full bg-[#AF4D98] md:h-[80vh]">
	<div class="mx-auto flex h-full flex-row items-center justify-center">
		<div class="mx-8 flex h-full w-full flex-col items-center justify-center">
			<h1 class="font-[Arvo] text-8xl font-bold text-[#F4E4BA] md:text-[9rem]">Fizzler</h1>
			<h2 class="text-center font-[Arvo] text-3xl text-[#F4E4BA] md:text-4xl">
				Make a Tauri app, Get a Fizzy Drink!
			</h2>
			<a
				class="mt-4 rounded-md bg-[#F4E4BA] p-4 font-[Arvo] text-2xl text-[#AF4D98]"
				href="https://hackclub.slack.com/archives/C09AD0R1SUV">Join <FizzlerSlackLink />!</a
			>
		</div>
	</div>
	<!-- <div class="absolute top-2/5 left-1/2 -translate-x-1/2 -translate-y-1/2"> -->
	<!-- 	<img src="bottle.svg" alt="bottle" class="size-[40rem] rotate-45" /> -->
	<!-- </div> -->
</div>

<div class="flex w-full flex-col justify-center bg-[#D66BA0] py-24 text-[#9DF7E5]">
	<div class="max-w-[60rem] md:mx-auto">
		<h1 class="mb-8 text-center font-[Arvo] text-6xl font-bold md:text-7xl">Instructions</h1>
		<ul class="mr-4 ml-8 flex list-disc flex-col gap-4 text-xl md:text-2xl">
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
				<a class="underline decoration-2" href="https://hackatime.hackclub.com/">Hackatime</a>
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

{#snippet questionSpacer(mobile)}
	<div
		class="mx-auto h-1 w-full max-w-2xl rounded-full bg-[#AF4D98] mask-radial-from-0 mask-radial-to-80% mask-radial-at-center
      {mobile ? 'md:hidden' : 'my-4'}
    "
	></div>
{/snippet}

<div class="flex w-full flex-col justify-center bg-[#9DF7E5] px-4 py-24 text-[#AF4D98]">
	<h1 class="mb-8 text-center font-[Arvo] text-7xl font-bold">FAQ</h1>
	<div class="flex w-full flex-col items-center justify-center gap-4 md:flex-row md:gap-8">
		<Question question="Can I submit an existing project?">
			<p>You need to create a new project for Fizzler, existing projects won't be accepted.</p>
		</Question>
		{@render questionSpacer(true)}
		<Question question="Can I submit my project for Summer of Making as well?">
			<p>Unfortunately, no...</p>
		</Question>
	</div>
	{@render questionSpacer(false)}
	<div class="flex w-full flex-col items-center justify-center gap-4 md:flex-row md:gap-8">
		<Question question="Is AI allowed?">
			<p>
				We advise against it, since it removes the fun of making it yourself, but if you do use it,
				you need to say so on your submission form.
			</p>
		</Question>
		{@render questionSpacer(true)}
		<Question question="What platforms do I make my app for?">
			<p>
				If you're making a desktop app then you only need one of Windows, MacOS, or Linux. If you're
				making a mobile app, then just Android. (IF IOS THEN REACH OUT TO US ON SLACK (<FizzlerSlackLink
				/>))
			</p>
		</Question>
	</div>
	{@render questionSpacer(false)}
	<div class="flex w-full flex-col items-center justify-center gap-4 md:flex-row md:gap-8">
		<Question question="Where can I learn Tauri?">
			<p>
				The <a href="https://v2.tauri.app/start/" class="underline decoration-2"> Tauri docs </a>
				provide a guide for creating a basic project, and you can look at
				<a href="https://github.com/Shuflduf/Tauri-Game-Launcher" class="underline decoration-2">
					the example project
				</a> for a complete example.
			</p>
		</Question>
		{@render questionSpacer(true)}
		<Question question="How do I host my app?">
			<p>
				<a
					class="underline decoration-2"
					href="https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository"
				>
					Github releases.
				</a>
			</p>
		</Question>
	</div>
</div>

<div class="flex w-full flex-col justify-center bg-[#F4E4BA] px-4 py-24 text-[#D66BA0]">
	<h1 class="mb-8 text-center font-[Arvo] text-7xl font-bold">Some Ideas</h1>
	<Ideas />
	<p class="mt-4 text-center text-xl font-bold">
		But feel free to do whatever you can think of. The crazier, the better!
	</p>
</div>

<div class="flex w-full flex-col justify-center bg-[#D66BA0] px-4 py-24 text-[#9DF7E5]">
	<h1 class="mb-8 text-center font-[Arvo] text-7xl font-bold">Get Started</h1>
	<h2 class="mb-8 text-center font-[Arvo] text-4xl">Resources</h2>
	<Resource
		name="Tauri Docs"
		imgPath="tauri.webp"
		link="https://v2.tauri.app/start/"
		flipped={false}
	>
		If you're just starting out, or you need a refresher on the basics, the Tauri docs are perfect
		for learning what the framework has to offer. Everything on the docs can be applied to your
		project!
	</Resource>
	<div
		class="mx-8 my-4 h-1 rounded-full bg-[#9DF7E5] mask-x-from-80% mask-x-to-100% md:hidden"
	></div>
	<Resource
		name="Example Project"
		imgPath="github.png"
		link="https://github.com/Shuflduf/Tauri-Game-Launcher"
		flipped={true}
	>
		Made with SvelteKit for the front-end, and TailwindCSS for styling. You can use it as a
		reference for more advanced uses of Tauri.
	</Resource>
	<div
		class="mx-8 my-4 h-1 rounded-full bg-[#9DF7E5] mask-x-from-80% mask-x-to-100% md:hidden"
	></div>
	<Resource
		name="Video Guide"
		imgPath="youtube.svg"
		link="https://www.youtube.com/watch?v=BGm0SCfY5Ak"
		flipped={false}
	>
		If you're more of a visual learner, then this guide by
		<a href="https://www.youtube.com/@codewithcon" class="underline decoration-2">Code with Con</a>
		is for you! It also covers all the prerequisites, such as Rust, and explains why Tauri is better
		than electron!
	</Resource>
	<h2 class="mt-16 mb-8 text-center font-[Arvo] text-4xl md:mt-0">Support</h2>
	<p class="mx-auto max-w-4xl text-center text-xl font-bold">
		If you need help with your project, or just want to talk about Tauri, feel free to talk to us at <FizzlerSlackLink
		/>, we'll be happy to help!
	</p>
</div>

<div
	class="flex w-full flex-row items-center justify-between bg-[#AF4D98] p-8 font-[Arvo] text-[#F4E4BA]"
>
	<div>
		<h1 class="text-3xl font-bold">Fizzler</h1>
		<a href="https://github.com/Shuflduf/fizzler" class="underline decoration-2">
			Site made with Love, Svelte, and Tailwind!
		</a>
	</div>
	&copy 2025 Hack Club
</div>
