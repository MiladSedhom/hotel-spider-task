<script lang="ts">
	import { Leaf, Menu, Phone, Search } from '@lucide/svelte'
</script>

<header class="h[var(--header-height)] text-fg shadow-[0_.25rem_.75rem_0_rgba(0,0,0,.04)]">
	<div class="container mx-auto flex justify-between py-5">
		<div class="flex gap-5">
			<Menu class=" h-6 w-6" />

			<img
				src="https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2024/09/FPJ-new.svg"
				alt="logo"
				width="259"
				height="15"
			/>
		</div>

		<nav>
			<ul class="flex gap-6 font-bold uppercase">
				<a class="underline-hover" href="/">room</a>
				<a class="underline-hover" href="/">dine</a>
				<a class="underline-hover" href="/">events</a>
				<a class="underline-hover" href="/">relax</a>
				<a class="underline-hover" href="/">music</a>
				<a class="underline-hover" href="/">shop</a>
			</ul>
		</nav>

		<div class="flex gap-4">
			<Search class="h-4 w-4" />
			<Phone class="h-4 w-4" />
			<Leaf class="h-4 w-4 " />
		</div>
	</div>
</header>
