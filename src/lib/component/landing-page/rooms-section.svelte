<script lang="ts">
	import { ChevronLeft, ChevronRight } from '@lucide/svelte'
	import { innerWidth } from 'svelte/reactivity/window'

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

	let itemsContainer = $state<HTMLDivElement | null>(null)
	let scrollLeft = $state(0)
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
<div
	class="flex overflow-hidden"
	bind:this={itemsContainer}
	onscroll={() => (scrollLeft = itemsContainer?.scrollLeft ?? 0)}
>
	{#each rooms as room, index}
		<div class="relative">
			<img class="min-w-screen" src={room.image} alt={room.title} loading="lazy" />

			<div class="absolute top-20 right-25 flex items-center gap-4 font-bold text-white">
				<button
					class="grid size-12 cursor-pointer place-items-center bg-white/30 text-white disabled:opacity-50"
					disabled={scrollLeft === 0}
					onclick={() => {
						if (!itemsContainer) return
						itemsContainer.scrollBy({
							left: -(innerWidth.current ?? 0),
							behavior: 'smooth',
						})
					}}
				>
					<ChevronLeft class="h-5 w-5" />
				</button>

				<span>{index + 1} / {rooms.length}</span>

				<button
					class="grid size-12 cursor-pointer place-items-center bg-white/30 text-white disabled:opacity-50"
					disabled={itemsContainer && scrollLeft === itemsContainer.scrollWidth - itemsContainer.clientWidth}
					onclick={() => {
						if (!itemsContainer) return
						itemsContainer.scrollBy({
							left: innerWidth.current ?? 0,
							behavior: 'smooth',
						})
					}}
				>
					<ChevronRight class="h-5 w-5" />
				</button>
			</div>

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
