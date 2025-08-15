<script lang="ts">
	import { ChevronLeft, ChevronRight } from '@lucide/svelte'
	import { onMount } from 'svelte'
	import Siema from 'siema'

	const items = Array.from({ length: 9 }, (_, i) => ({
		id: i,
		logo: 'https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2024/09/bohemia-logo.svg',
		video: 'https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2025/01/AA-1-Bohemia-Front-Video.mp4',
	}))

	let siema = $state<Siema | null>(null)
	let currentSlide = $state(0)

	onMount(() => {
		siema = new Siema({
			selector: '#its-play-time-siema',
			duration: 300,
			easing: 'ease-out',
			perPage: {
				1200: 3.75,
				800: 3.2,
				600: 2.5,
				0: 2.2,
			},
			startIndex: 0,
			draggable: true,
			multipleDrag: true,
			threshold: 20,
			loop: false,
			rtl: false,
			onInit: () => {
				currentSlide = siema?.currentSlide ?? 0
			},
			onChange: () => {
				currentSlide = siema?.currentSlide ?? 0
			},
		})

		return () => {
			siema?.destroy()
		}
	})

	function goToPrev() {
		siema?.prev()
	}

	function goToNext() {
		siema?.next()
	}
</script>

<section class="container mx-auto px-4 py-8 text-fg sm:px-6 sm:py-12 lg:px-10 lg:py-20">
	<div class="flex flex-col items-start justify-between gap-4 sm:flex-row sm:items-center">
		<h3 class="text-2xl font-bold uppercase sm:text-3xl lg:text-[3rem]">it's playtime</h3>
		<div class="flex items-center gap-2">
			<button
				class="grid size-12 cursor-pointer place-items-center bg-[#f2f2f2] disabled:opacity-50 sm:size-14"
				disabled={currentSlide === 0}
				onclick={goToPrev}
			>
				<ChevronLeft class="h-5 w-5 sm:h-6 sm:w-6" />
			</button>
			<button
				class="grid size-12 cursor-pointer place-items-center bg-[#f2f2f2] disabled:opacity-50 sm:size-14"
				disabled={siema && currentSlide >= items.length - 1}
				onclick={goToNext}
			>
				<ChevronRight class="h-5 w-5 sm:h-6 sm:w-6" />
			</button>
		</div>
	</div>

	<div id="its-play-time-siema" class="gap-3 lg:gap-6">
		{#each items as item}
			<div class="flex flex-col items-center gap-3 px-2 lg:gap-5">
				<img
					src={item.logo}
					alt="some logo"
					class="h-auto w-32 lg:w-40"
					width="160"
					height="90"
					draggable={false}
				/>
				<video
					src={item.video}
					autoplay
					loop
					muted
					class=" aspect-video h-80 w-full bg-fg object-cover lg:h-100 lg:w-auto"
				></video>
			</div>
		{/each}
	</div>

	<span class="mt-8 block h-[1px] bg-fg sm:mt-12 lg:mt-20"></span>

	<div class="flex flex-col justify-between gap-6 py-6 sm:py-8 lg:flex-row lg:gap-8 lg:py-10">
		<h4
			class="max-w-full text-2xl leading-tight font-bold text-wrap uppercase sm:text-3xl lg:max-w-[20ch] lg:text-[3rem] lg:leading-[3rem]"
		>
			A CELEBRATORY EXPERIENCE
		</h4>
		<p class="max-w-full text-sm font-medium opacity-75 sm:text-base lg:max-w-[70ch]">
			Dubbed the Hottest Hotel in Dubai, Indulge Yourself at our Dare-to-be-Different Immersive Playground.
			Rediscover your Senses with our nonstop entertainment lineup, award-winning dining, top nightlife,
			industry-leading spa sanctuary, and our 150-metre private beach. Be Seen, Be Snapped, and Come Play at Palm
			Jumeirah's Most Talked-About Resort.
		</p>
	</div>
</section>
