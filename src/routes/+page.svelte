<script lang="ts">
	import FloatingButtons from '$lib/component/landing-page/floating-buttons.svelte'
	import Header from '$lib/component/landing-page/header.svelte'
	import ItsPlayTimeSection from '$lib/component/landing-page/its-play-time-section.svelte'
	import RoomsSection from '$lib/component/landing-page/rooms-section.svelte'
	import ChevronDown from '@lucide/svelte/icons/chevron-down'
	import ChevronRight from '@lucide/svelte/icons/chevron-right'
</script>

<Header />

<main class="bg-white">
	<!-- hero -->
	<section class="container mx-auto grid min-h-[100dvh] items-center px-4 py-12 text-fg lg:px-35 lg:py-40">
		<h1 class="flex flex-col items-center justify-between gap-4 sm:flex-row sm:items-start sm:gap-8">
			<span class="text-6xl font-bold uppercase sm:text-8xl lg:text-[10rem]">stay</span>
			<div class="text-center sm:text-right">
				<span class="text-6xl font-bold uppercase sm:text-8xl lg:text-[10rem]">play</span>
				<p class="text-sm font-bold whitespace-pre-line uppercase lg:text-[1.5rem]">
					Come play at Dubai's <br />hottest beach hotel
				</p>
			</div>
		</h1>
		<div class="mt-8 flex justify-center">
			<a
				class="flex cursor-pointer flex-col items-center justify-center text-base font-bold uppercase sm:text-lg lg:text-[1.5rem]"
				href="#ticker"
			>
				Explore
				<ChevronDown class="h-5 w-5 sm:h-6 sm:w-6" />
			</a>
		</div>
	</section>

	<!-- ticker -->
	<section id="ticker" class="text-fg">
		<ul class="overflow-hidden">
			<div class="flex animate-marquee [animation-direction:reverse]">
				{#each { length: 300 } as _}
					<li class="block min-w-[7rem] text-sm font-bold uppercase sm:text-base lg:min-w-[8rem]">
						come play
						<ChevronRight class="inline h-4 w-4 sm:h-5 sm:w-5" />
					</li>
				{/each}
			</div>
		</ul>

		<div class="flex gap-4 overflow-x-auto bg-black p-4 sm:gap-8 sm:p-6 lg:gap-18 lg:p-10">
			{#each { length: 6 } as _}
				<img
					src="https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2025/01/25.11.24-FIVE-WEB-PALM-AWARDS-4-1.svg"
					alt="some logo"
					class="h-16 w-auto flex-shrink-0 sm:h-20 lg:h-auto lg:w-[150px]"
					width="150"
					height="186"
				/>
			{/each}
		</div>

		<ul class="overflow-hidden">
			<div class="flex animate-marquee">
				{#each { length: 300 } as _}
					<li class="block min-w-[7rem] text-sm font-bold uppercase sm:text-base lg:min-w-[8rem]">
						come play
						<ChevronRight class="inline h-4 w-4 sm:h-5 sm:w-5" />
					</li>
				{/each}
			</div>
		</ul>
	</section>

	<!-- room offers-->
	<section
		class="flex flex-col items-center bg-[linear-gradient(90deg,rgba(216,154,202,1)_0%,rgba(230,219,174,1)_0%,rgba(225,202,201,1)_50%,rgba(225,156,199,1)_100%)] px-4 py-8 text-white sm:py-16 lg:py-35"
	>
		<h2
			class="max-w-4xl text-center text-2xl leading-tight font-bold whitespace-pre-line sm:text-3xl md:text-4xl lg:text-[4.5rem] lg:leading-[4.5rem]"
		>
			DUBAI'S HOTTEST<br />BEACH HOTEL
		</h2>
		<p class="mt-4 max-w-4xl px-4 text-center text-sm font-medium whitespace-pre-line sm:text-base lg:text-[1rem]">
			Luxury rooms and suites. 150-m private beach. Picture perfect pools. Insta-views. Award-winning restaurants.
			Stunning spa. Our unashamedly luxurious resort has it all!
		</p>
		<p class="mt-2 text-center text-sm font-bold sm:text-base lg:text-[1rem]">
			Enjoy complimentary group yoga with all room bookings.
		</p>

		<div class="container mx-auto mt-6 bg-white p-4 text-fg sm:mt-8 sm:p-5 lg:mt-10">
			<h3 class="text-center text-lg font-bold sm:text-xl lg:text-[1.75rem]">ROOM OFFERS AT FIVE</h3>
			<div class="my-4 flex flex-col gap-4 sm:my-5 sm:flex-row sm:gap-5">
				{#each { length: 3 }}
					<div class="flex flex-col items-center gap-3 sm:gap-4">
						<div class="group h-[200px] w-full overflow-hidden sm:h-[240px] sm:w-100 lg:h-[270px]">
							<img
								class="h-full w-full object-cover transition-all group-hover:scale-110"
								src="https://palmjumeirah.fivehotelsandresorts.com/wp-content/webp-express/webp-images/doc-root/wp-content/uploads/2025/06/SEVENROOMS-BG.jpg.webp"
								alt=""
							/>
						</div>
						<a href="/" class="underline-hover text-center text-base font-bold sm:text-lg lg:text-[1.75rem]"
							>PAY 3 STAY 4 OFFER</a
						>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<ItsPlayTimeSection />

	<RoomsSection />

	<FloatingButtons />
</main>

<footer class="sticky bottom-0 -z-10 flex h-screen flex-col items-center justify-center bg-white p-4 text-fg">
	<h1 class="text-center text-[3.25rem] leading-[1em] font-black lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class="text-center text-[3.25rem] leading-[1em] font-black lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class="text-center text-[3.25rem] leading-[1em] font-black lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class="text-center text-[3.25rem] leading-[1em] font-black lg:text-[9.5rem]">COME PLAY FIVE</h1>

	<h1 class=" text-center text-[3.25rem] leading-[1em] font-black md:hidden lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class=" text-center text-[3.25rem] leading-[1em] font-black md:hidden lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class=" text-center text-[3.25rem] leading-[1em] font-black md:hidden lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class=" text-center text-[3.25rem] leading-[1em] font-black md:hidden lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class=" text-center text-[3.25rem] leading-[1em] font-black md:hidden lg:text-[9.5rem]">COME PLAY FIVE</h1>
	<h1 class=" text-center text-[3.25rem] leading-[1em] font-black md:hidden lg:text-[9.5rem]">COME PLAY FIVE</h1>
</footer>
