<script>
	import SlackLink from '$lib/SlackLink.svelte';
</script>

<div class="h-[35rem] w-full bg-[#CEB1BE]">
	<div class="mx-auto flex h-full w-7xl flex-row items-center">
		<div class="flex h-full w-full flex-col items-center justify-center">
			<h1 class="font-[Arvo] text-9xl font-bold text-[#2D2D34]">Fizzler</h1>
			<h2 class="font-[Arvo] text-4xl text-[#2D2D34]">Make a Tauri app, Get a fizzy drink!</h2>
		</div>
		<div class="h-full w-full"></div>
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
				<b>Submit your project to earn a <i>Fizzy Drink</i>:</b> Minimum 5 hours, tracked with Hackatime
			</li>
			<li>
				<b>
					Show off your drink in
					<SlackLink link="https://hackclub.slack.com/archives/C09AD0R1SUV">#fizzlers</SlackLink>:
				</b> Pepsi, Monster, some obscure energy drink, pretty much anything that you SHOULDN'T shake
				before opening
			</li>
		</ul>
	</div>
</div>
<div class="h-1 w-full bg-[#B97375]"></div>
