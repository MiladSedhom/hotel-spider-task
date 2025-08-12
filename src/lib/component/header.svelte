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
				<li>{@render link('/', 'room')}</li>
				<li>{@render link('/', 'dine')}</li>
				<li>{@render link('/', 'events')}</li>
				<li>{@render link('/', 'relax')}</li>
				<li>{@render link('/', 'music')}</li>
				<li>{@render link('/', 'shop')}</li>
			</ul>
		</nav>

		<div class="flex gap-4">
			<Search class="h-4 w-4" />
			<Phone class="h-4 w-4" />
			<Leaf class="h-4 w-4 " />
		</div>
	</div>
</header>

{#snippet link(href: string, text: string)}
	<a
		class="relative after:absolute after:right-0 after:-bottom-1 after:left-0 after:h-0.5 after:origin-bottom-right after:scale-x-0 after:bg-current after:transition-transform after:duration-300 after:content-[''] hover:after:origin-bottom-left hover:after:scale-x-100"
		{href}>{text}</a
	>
{/snippet}
