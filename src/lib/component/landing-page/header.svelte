<script lang="ts">
	import { Leaf, Phone, Search } from '@lucide/svelte'
	import { fade } from 'svelte/transition'

	let lastScrollY = $state(0)
	let isScrollingUp = $state(true)
	let isMenuOpen = $state(false)

	const navLinks = [
		{ name: 'room', href: '/' },
		{ name: 'dine', href: '/' },
		{ name: 'events', href: '/' },
		{ name: 'relax', href: '/' },
		{ name: 'music', href: '/' },
		{ name: 'shop', href: '/' },
	]

	function toggleMenu() {
		isMenuOpen = !isMenuOpen
	}
</script>

<svelte:window
	onscroll={e => {
		if (isMenuOpen) return
		if (window.scrollY < lastScrollY) isScrollingUp = true
		else isScrollingUp = false
		lastScrollY = window.scrollY
	}}
/>

<header
	class="h[var(--header-height)] top-0 z-50 w-full bg-white text-fg shadow-[0_.25rem_.75rem_0_rgba(0,0,0,.04)] transition-all data-[scrolling-up=true]:fixed data-[scrolling-up=true]:animate-slide-down"
	data-scrolling-up={isScrollingUp}
>
	<div class="container mx-auto flex justify-between py-5">
		<div class="flex gap-5">
			<button
				class="hamburger-menu relative flex h-6 w-6 cursor-pointer items-center justify-center"
				aria-label="Toggle menu"
				class:active={isMenuOpen}
				onclick={toggleMenu}
			>
				<span class="hamburger-line"></span>
			</button>

			<img
				src="https://palmjumeirah.fivehotelsandresorts.com/wp-content/uploads/2024/09/FPJ-new.svg"
				alt="logo"
				width="259"
				height="15"
			/>
		</div>

		<nav class="hidden md:block">
			<ul class="flex gap-6 font-bold uppercase">
				{#each navLinks as link}
					<a
						class="underline-hover transition-opacity duration-300"
						class:opacity-0={isMenuOpen}
						class:opacity-100={!isMenuOpen}
						href={link.href}
					>
						{link.name}
					</a>
				{/each}
			</ul>
		</nav>

		<div class="flex gap-4">
			<Search class="h-4 w-4" />
			<Phone class="h-4 w-4" />
			<Leaf class="h-4 w-4 " />
		</div>
	</div>
</header>

{#if isMenuOpen}
	<div class="fixed inset-0 z-30 flex justify-between bg-white px-20" transition:fade={{ duration: 300 }}>
		<div class="flex h-full flex-col items-start justify-center">
			<nav>
				<ul class="space-y-8 text-start">
					{#each navLinks as link, i (link.name)}
						<li>
							<a
								class="menu-item block text-4xl font-bold uppercase transition-opacity hover:opacity-70"
								href={link.href}
								onclick={() => (isMenuOpen = false)}
								style="--delay: {i * 0.1 + 0.2}s"
							>
								{link.name}
							</a>
						</li>
					{/each}
				</ul>
			</nav>
		</div>
		<div class="h-full w-100 pt-20 pb-10">
			<div class="h-full bg-fg"></div>
		</div>
	</div>
{/if}

<style>
	.hamburger-line {
		position: relative;
		width: 1.5rem;
		height: 0;
	}

	.hamburger-line::before,
	.hamburger-line::after {
		content: '';
		position: absolute;
		left: 0;
		width: 100%;
		height: 2px;
		background-color: currentColor;
		transition: all 0.3s ease;
	}

	.hamburger-line::before {
		top: -3px;
	}

	.hamburger-line::after {
		top: 3px;
	}

	.hamburger-menu.active .hamburger-line::before {
		top: 0;
		transform: rotate(405deg);
	}

	.hamburger-menu.active .hamburger-line::after {
		top: 0;
		transform: rotate(-405deg);
	}

	.menu-item {
		opacity: 0;
		transform: translateY(30px);
		animation: slideInUp 200ms ease-out var(--delay) forwards;
	}

	@keyframes slideInUp {
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}
</style>
