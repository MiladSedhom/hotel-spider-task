<script lang="ts">
	import { ChevronLeft, ChevronRight } from '@lucide/svelte'

	let itemsContainer = $state<HTMLDivElement | null>(null)
	let scrollLeft = $state(0)

	const SCROLL_DISTANCE = 274
</script>

<section class="container mx-auto px-10 py-20 text-fg">
	<div class="flex justify-between">
		<h3 class=" text-[3rem] font-bold uppercase">it’s playtime</h3>
		<div class="flex items-center gap-2">
			<button
				class="grid size-14 cursor-pointer place-items-center bg-[#f2f2f2] disabled:opacity-50"
				disabled={scrollLeft === 0}
				onclick={() => {
					if (!itemsContainer) return
					itemsContainer.scrollBy({
						left: -SCROLL_DISTANCE,
						behavior: 'smooth',
					})
				}}
			>
				<ChevronLeft class="h-6 w-6" />
			</button>
			<button
				class="grid size-14 cursor-pointer place-items-center bg-[#f2f2f2]"
				disabled={itemsContainer && scrollLeft === itemsContainer.scrollWidth - itemsContainer.clientWidth}
				onclick={() => {
					if (!itemsContainer) return
					itemsContainer.scrollBy({
						left: SCROLL_DISTANCE,
						behavior: 'smooth',
					})
				}}
			>
				<ChevronRight class="h-6 w-6" />
			</button>
		</div>
	</div>

	<div
		class="flex gap-6 overflow-hidden"
		bind:this={itemsContainer}
		onscroll={() => (scrollLeft = itemsContainer?.scrollLeft ?? 0)}
	>
		{#each { length: 9 }}
			<div class="flex flex-col items-center gap-5">
				<img
					src="https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2024/09/bohemia-logo.svg"
					alt="some logo"
					width="160"
					height="90"
				/>
				<div class="h-100 w-63.25 bg-fg"></div>
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
