<script>
	import '../app.css';
	import { slide } from 'svelte/transition';

	let { children } = $props();

	let menuOpen = $state(false)
</script>

<div class="flex flex-col min-h-screen  bg-gray-400">
	
	<nav class="flex justify-between items-center px-8 py-3 bg-gray-900">
		<div class="h-13 w-13">
			<img src="./favicon.png" alt="">
		</div>
		
		<ul class="hidden md:flex gap-4 text-gray-100">
			<li>Holaaa</li>
			<li>Necesito</li>
			<li>Más</li>
		</ul>

		<button class="md:hidden text-gray-50" onclick={() => menuOpen = !menuOpen} aria-label="Hamburger">
			<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					stroke="currentColor"
					stroke-width="2"
					class="w-6 h-6 transition-transform duration-300"
					class:rotate-90={menuOpen}
				>
				<line x1="4" y1="6" x2="20" y2="6" />
				<line x1="4" y1="12" x2="20" y2="12" />
				<line x1="4" y1="18" x2="20" y2="18" />
			</svg>
		</button>
		
	</nav>

	{#if menuOpen}
	<ul class="flex flex-col bg-gray-700 text-gray-400 p-2 gap-2 text-center rounded-b-lg" in:slide={{ duration: 400 }} out:slide={{ duration: 400 }}>
		<li>Uno</li>
		<li>Dos</li>

	</ul>
	{/if}
	
	
	{@render children()}


	<footer class="mt-auto flex justify-center gap-4">
		<p>2025	</p>
		<p>Hecho por icarus.mx</p>
	</footer>
</div>