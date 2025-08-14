<script lang="ts">
	import { ChevronLeft, ChevronRight } from '@lucide/svelte'
	import { onMount } from 'svelte'
	import Siema from 'siema'

	const items = Array.from({ length: 9 }, (_, i) => ({
		id: i,
		logo: 'https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2024/09/bohemia-logo.svg',
		video: 'https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2025/01/AA-1-Bohemia-Front-Video.mp4',
	}))

	let siemaContainer: HTMLDivElement
	let siema: Siema
	let currentSlide = $state(0)

	onMount(() => {
		siema = new Siema({
			selector: siemaContainer,
			duration: 300,
			easing: 'ease-out',
			perPage: {
				1200: 4,
				800: 3,
				600: 2,
				0: 1,
			},
			startIndex: 0,
			draggable: true,
			multipleDrag: true,
			threshold: 20,
			loop: false,
			rtl: false,
			onInit: () => {
				currentSlide = siema.currentSlide
			},
			onChange: () => {
				currentSlide = siema.currentSlide
			},
		})

		return () => {
			siema.destroy()
		}
	})

	function goToPrev() {
		siema.prev()
	}

	function goToNext() {
		siema.next()
	}
</script>

<section class="container mx-auto px-10 py-20 text-fg">
	<div class="flex justify-between">
		<h3 class=" text-[3rem] font-bold uppercase">it’s playtime</h3>
		<div class="flex items-center gap-2">
			<button
				class="grid size-14 cursor-pointer place-items-center bg-[#f2f2f2] disabled:opacity-50"
				disabled={currentSlide === 0}
				onclick={goToPrev}
			>
				<ChevronLeft class="h-6 w-6" />
			</button>
			<button
				class="grid size-14 cursor-pointer place-items-center bg-[#f2f2f2] disabled:opacity-50"
				disabled={siema && currentSlide >= items.length - 1}
				onclick={goToNext}
			>
				<ChevronRight class="h-6 w-6" />
			</button>
		</div>
	</div>

	<div bind:this={siemaContainer} class="gap-6">
		{#each items as item}
			<div class="flex flex-col items-center gap-5 px-3">
				<img src={item.logo} alt="some logo" width="160" height="90" draggable={false} />
				<video src={item.video} autoplay loop muted class=" h-100 w-63.25 bg-fg object-cover"></video>
			</div>
		{/each}
	</div>

	<span class="mt-20 block h-[1px] bg-fg"></span>

	<div class="flex justify-between py-10">
		<h4 class="max-w-[20ch] text-[3rem] leading-[3rem] font-bold text-wrap uppercase">A CELEBRATORY EXPERIENCE</h4>
		<p class="max-w-[70ch] font-medium opacity-75">
			Dubbed the Hottest Hotel in Dubai, Indulge Yourself at our Dare-to-be-Different Immersive Playground.
			Rediscover your Senses with our nonstop entertainment lineup, award-winning dining, top nightlife,
			industry-leading spa sanctuary, and our 150-metre private beach. Be Seen, Be Snapped, and Come Play at Palm
			Jumeirah’s Most Talked-About Resort.
		</p>
	</div>
</section>
