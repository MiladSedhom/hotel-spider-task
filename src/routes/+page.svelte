<script>
	import Header from '$lib/component/header.svelte'
	import ChevronDown from '@lucide/svelte/icons/chevron-down'
	import ChevronRight from '@lucide/svelte/icons/chevron-right'
</script>

<Header />

<section class="container mx-auto grid h-[calc(100dvh-var(--header-height))] items-center pb-35 text-fg">
	<h1 class="flex items-center justify-between px-35">
		<span class="text-[10rem] font-bold uppercase">stay</span>
		<div>
			<span class="text-[10rem] font-bold uppercase">play</span>
			<p class="ms-3 -mt-12 text-[1.5rem] font-bold whitespace-pre-line uppercase">
				Come play at Dubai's &#10; hottest beach hotel
			</p>
		</div>
	</h1>
	<div class="flex justify-center">
		<a
			class="flex cursor-pointer flex-col items-center justify-center text-[1.5rem] font-bold uppercase"
			href="#ticker"
		>
			Explore
			<ChevronDown class="h-6 w-6" />
		</a>
	</div>
</section>

<section id="ticker" class=" h-[calc(100dvh-var(--header-height))] text-fg [animation-direction:reverse]">
	<ul class=" overflow-hidden">
		<div class="flex animate-marquee">
			{#each { length: 300 } as _}
				<li class="block min-w-[8rem] font-bold uppercase">
					click play
					<ChevronRight class="inline h-5 w-5" />
				</li>
			{/each}
		</div>
	</ul>

	<div class="flex gap-18 bg-black p-10">
		{#each { length: 6 } as _}
			<img
				src="https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2025/01/25.11.24-FIVE-WEB-PALM-AWARDS-4-1.svg"
				alt="some logo"
				width="150"
				height="186"
			/>
		{/each}
	</div>

	<ul class=" overflow-hidden">
		<div class="flex animate-marquee">
			{#each { length: 300 } as _}
				<li class="block min-w-[8rem] font-bold uppercase">
					click play
					<ChevronRight class="inline h-5 w-5" />
				</li>
			{/each}
		</div>
	</ul>
</section>
