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

	let siemaContainer: HTMLDivElement
	let siema: Siema | null = $state(null)
	let currentSlide = $state(0)

	onMount(() => {
		siema = new Siema({
			selector: siemaContainer,
			duration: 200,
			easing: 'ease-out',
			perPage: 1,
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

<div class="flex items-center justify-between bg-black p-20 text-white">
	<h3 class=" text-[10rem] leading-[1em] font-bold uppercase">rooms</h3>
	<div class="flex flex-col gap-4">
		<p class="text-[1.5rem] font-medium">Lifestyle Meets Luxury</p>
		<a class="font-bold uppercase" href="/"
			>all rooms
			<ChevronRight class="inline h-5 w-5" />
		</a>
	</div>
</div>
<div class="relative">
	<div bind:this={siemaContainer}>
		{#each rooms as room, index}
			<div class="relative">
				<img class="h-auto w-screen" src={room.image} alt={room.title} loading="lazy" draggable={false} />

				<div class="absolute bottom-20 left-25 space-y-4">
					<h4 class="text-[2.5rem] font-bold text-white uppercase">{room.title}</h4>
					<a
						href={room.link}
						class="flex w-fit items-center bg-black px-4 py-2 text-[1.25rem] font-bold text-white uppercase"
					>
						Explore
						<ChevronRight class="inline h-5 w-5" />
					</a>
				</div>
			</div>
		{/each}
	</div>

	<div class="absolute top-20 right-25 z-10 flex items-center gap-4 font-bold text-white">
		<button
			class="grid size-12 cursor-pointer place-items-center bg-white/30 text-white hover:bg-white/50 disabled:opacity-50"
			disabled={currentSlide === 0}
			onclick={goToPrev}
		>
			<ChevronLeft class="h-5 w-5" />
		</button>

		<span>{currentSlide + 1} / {rooms.length}</span>

		<button
			class="grid size-12 cursor-pointer place-items-center bg-white/30 text-white hover:bg-white/50 disabled:opacity-50"
			disabled={currentSlide === rooms.length - 1}
			onclick={goToNext}
		>
			<ChevronRight class="h-5 w-5" />
		</button>
	</div>
</div>
