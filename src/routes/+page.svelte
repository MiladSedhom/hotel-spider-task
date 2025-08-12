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
				Come play at Dubai’s &#10; hottest beach hotel
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

<section
	class="flex flex-col items-center bg-[linear-gradient(90deg,rgba(216,154,202,1)_0%,rgba(230,219,174,1)_0%,rgba(225,202,201,1)_50%,rgba(225,156,199,1)_100%)] py-35 text-white"
>
	<h2 class="text-center text-[4.5rem] leading-[4.5rem] font-bold whitespace-pre-line">
		DUBAI’S HOTTEST &#10; BEACH HOTEL
	</h2>
	<p class="text-center text-[1rem] font-medium whitespace-pre-line">
		Luxury rooms and suites. 150-m private beach. Picture perfect pools. Insta-views. Award-winning restaurants.
		Stunning spa. Our unashamedly luxurious resort has it all!
	</p>
	<p class="text-center text-[1rem] font-bold">Enjoy complimentary group yoga with all room bookings.</p>

	<div class="container mx-auto mt-10 bg-white p-5 text-fg">
		<h3 class="text-center text-[1.75rem] font-bold">ROOM OFFERS AT FIVE</h3>
		<div class="my-5 flex gap-5">
			{#each { length: 3 }}
				<div class="flex flex-col items-center gap-4">
					<img
						src="https://palmjumeirah.fivehotelsandresorts.com/wp-content/webp-express/webp-images/doc-root/wp-content/uploads/2025/06/SEVENROOMS-BG.jpg.webp"
						alt=""
						width="400"
						height="270"
					/>
					<p class="text-center text-[1.75rem] font-bold">PAY 3 STAY 4 OFFER</p>
				</div>
			{/each}
		</div>
	</div>
</section>
