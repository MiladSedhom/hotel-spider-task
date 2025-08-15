<script lang="ts">
	import { ChevronLeft, ChevronRight } from '@lucide/svelte'
	import { onMount } from 'svelte'
	import Siema from 'siema'

	const rooms = [
		{
			title: 'Superior',
			image: 'https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2024/06/10300060-HDR-Edit-1-1400x933.webp',
			link: '/',
		},
		{
			title: 'Superior | Twin Beds',
			image: 'https://palmjumeirah.fivehotelsandresorts.com/wp-content/webp-express/webp-images/doc-root/wp-content/uploads/2024/06/03-SUP-TT-1-1400x926.jpg.webp',
			link: '/',
		},
		{
			title: 'Superior| Double Queen',
			image: 'https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2024/06/Superior-Double-Queen-1920x1280.webp',
			link: '/',
		},
	]

	let siema = $state<Siema | null>(null)
	let currentSlide = $state(0)

	onMount(() => {
		siema = new Siema({
			selector: '#rooms-siema',
			duration: 300,
			easing: 'ease-out',
			perPage: {
				800: 1,

				0: 1.2,
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
		console.log('goToPrev called, siema:', siema)
		if (siema) {
			siema.prev()
			console.log('prev() called, new slide:', siema.currentSlide)
		}
	}

	function goToNext() {
		console.log('goToNext called, siema:', siema)
		if (siema) {
			siema.next()
			console.log('next() called, new slide:', siema.currentSlide)
		}
	}
</script>

<div
	class="flex flex-col items-start justify-between gap-4 bg-black p-4 text-white sm:flex-row sm:items-center sm:gap-8 sm:p-8 lg:p-20"
>
	<h3 class="text-4xl leading-[1em] font-bold uppercase sm:text-6xl md:text-8xl lg:text-[10rem]">rooms</h3>
	<div class="flex flex-col gap-3 sm:gap-4">
		<p class="text-lg font-medium sm:text-xl lg:text-[1.5rem]">Lifestyle Meets Luxury</p>
		<a class="text-sm font-bold uppercase sm:text-base" href="/"
			>all rooms
			<ChevronRight class="inline h-4 w-4 sm:h-5 sm:w-5" />
		</a>
	</div>
</div>
<div class="relative bg-black p-4">
	<div id="rooms-siema">
		{#each rooms as room, index}
			<div class="relative max-sm:me-4">
				<img
					class="h-120 w-auto object-cover md:h-auto md:w-screen"
					src={room.image}
					alt={room.title}
					loading="lazy"
					draggable={false}
				/>

				<div
					class="absolute bottom-4 left-4 space-y-2 sm:bottom-8 sm:left-8 sm:space-y-3 lg:bottom-20 lg:left-25 lg:space-y-4"
				>
					<h4 class="text-lg font-bold text-white uppercase sm:text-2xl lg:text-[2.5rem]">{room.title}</h4>
					<a
						href={room.link}
						class="flex w-fit items-center bg-black px-3 py-2 text-sm font-bold text-white uppercase sm:px-4 sm:text-base lg:text-[1.25rem]"
					>
						Explore
						<ChevronRight class="inline h-4 w-4 sm:h-5 sm:w-5" />
					</a>
				</div>
			</div>
		{/each}
	</div>

	<div
		class="top-4 right-4 z-10 flex items-center justify-center gap-2 font-bold text-white max-md:mt-4 sm:top-8 sm:right-8 sm:gap-3 md:absolute lg:top-20 lg:right-25 lg:gap-4"
	>
		<button
			class="grid size-10 cursor-pointer place-items-center bg-white/30 text-white hover:bg-white/50 disabled:opacity-50 sm:size-12"
			disabled={currentSlide === 0}
			onclick={goToPrev}
		>
			<ChevronLeft class="h-4 w-4 sm:h-5 sm:w-5" />
		</button>

		<span class="text-sm sm:text-base">{currentSlide + 1} / {rooms.length}</span>

		<button
			class="grid size-10 cursor-pointer place-items-center bg-white/30 text-white hover:bg-white/50 disabled:opacity-50 sm:size-12"
			disabled={currentSlide === rooms.length - 1}
			onclick={goToNext}
		>
			<ChevronRight class="h-4 w-4 sm:h-5 sm:w-5" />
		</button>
	</div>
</div>
