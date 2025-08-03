<script>
	import '../app.css';
	import { slide } from 'svelte/transition';
  import { injectAnalytics } from '@vercel/analytics/sveltekit';


  
	let { children } = $props();
  let menuOpen = $state(false)
  const year = new Date().getFullYear();
  
  injectAnalytics();

</script>

<div class="flex flex-col min-h-screen bg-primary-50">
	
	<nav class="flex justify-between items-center px-8 py-4 shadow-sm border-b border-primary-200 bg-secondary-800">
		<!-- Desktop: Logo + Text -->
		<div class="hidden md:flex items-center gap-3">
			<div class="h-12 w-12">
				<img src="./favicon.png" alt="Entrelazadas" class="h-full w-full object-contain">
			</div>
			<div>
				<h1 class="font-primary font-bold text-primar-100 text-lg">Entrelazadas</h1>
				<p class="font-secondary text-primary-300 text-xs">No estamos solas A.C.</p>
			</div>
		</div>
		
		<!-- Mobile: Prominent Logo + Text + Hamburger -->
		<div class="md:hidden flex justify-between items-center w-full py-3">
			<div class="flex items-center gap-3">
				<div class="h-10 w-10 flex-shrink-0">
					<img src="./favicon.png" alt="Entrelazadas" class="h-full w-full object-contain">
				</div>
				<div>
					<h1 class="font-primary font-bold text-primary-100 text-lg leading-tight">Entrelazadas</h1>
					<p class="font-secondary text-primary-300 text-xs leading-tight">No estamos solas A.C.</p>
				</div>
			</div>
			<button class="text-primary-300 p-2 -mr-2" onclick={() => menuOpen = !menuOpen} aria-label="Menú">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 24 24"
					stroke="currentColor"
					stroke-width="2"
					class="w-6 h-6"
				>
					<line x1="4" y1="6" x2="20" y2="6" />
					<line x1="4" y1="12" x2="20" y2="12" />
					<line x1="4" y1="18" x2="20" y2="18" />
				</svg>
			</button>
		</div>
		
		<ul class="hidden md:flex gap-8 text-primary-800 font-secondary">
			<li><a href="/" class="hover:text-secondary-600 transition-colors">Inicio</a></li>
			<li><a href="/servicios" class="hover:text-secondary-600 transition-colors">Servicios</a></li>
			<li><a href="/recursos" class="hover:text-secondary-600 transition-colors">Recursos</a></li>
			<li><a href="/contacto" class="hover:text-secondary-600 transition-colors">Contacto</a></li>
		</ul>
		
	</nav>

	{#if menuOpen}
	<ul class="flex flex-col bg-white border-b border-primary-100 text-primary-700 p-4 gap-4 shadow-sm font-secondary" in:slide={{ duration: 300 }} out:slide={{ duration: 300 }}>
		<li><a href="/" class="block hover:text-primary-500 transition-colors">Inicio</a></li>
		<li><a href="/servicios" class="block hover:text-primary-500 transition-colors">Servicios</a></li>
		<li><a href="/recursos" class="block hover:text-primary-500 transition-colors">Recursos</a></li>
		<li><a href="/contacto" class="block hover:text-primary-500 transition-colors">Contacto</a></li>

	</ul>
	{/if}
	
	
	{@render children()}

<footer class="bg-gradient-to-b from-gray-800 to-gray-900 text-gray-300 mt-12">
  <div class="max-w-6xl mx-auto px-6 py-12 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
    
    <!-- About Us -->
    <div>
      <h2 class="text-lg font-bold mb-4 text-white">Entrelazadas A.C.</h2>
      <p class="text-sm leading-relaxed mb-4">
        Organización civil comprometida con erradicar la violencia de género a través del apoyo psicológico y legal integral.
      </p>
      <p class="text-xs text-gray-400">
        🔒 Todos nuestros servicios son confidenciales y gratuitos.
      </p>
    </div>

    <!-- Quick Links -->
    <div>
      <h2 class="text-lg font-bold mb-4 text-white">Enlaces rápidos</h2>
      <ul class="space-y-2 text-sm">
        <li><a href="/servicios" class="hover:text-primary-300 transition-colors">Nuestros servicios</a></li>
        <li><a href="/recursos" class="hover:text-primary-300 transition-colors">Recursos útiles</a></li>
        <li><a href="/contacto" class="hover:text-primary-300 transition-colors">Contacto</a></li>
        <li><a href="/blog" class="hover:text-primary-300 transition-colors">Blog</a></li>
      </ul>
    </div>


    <!-- Social Media -->
    <div>
      <h2 class="text-lg font-bold mb-4 text-white">Síguenos</h2>
      <div class="flex gap-4 mb-4">
        <a href="https://www.facebook.com/EntrelazadasAC/" aria-label="Facebook" class="hover:text-primary-300 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
            <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
          </svg>
        </a>
        <button aria-label="Instagram" class="hover:text-primary-300 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
            <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
          </svg>
        </button>
        <button aria-label="Twitter" class="hover:text-primary-300 transition-colors">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
            <path d="M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z"/>
          </svg>
        </button>
      </div>
      <p class="text-xs text-gray-400">
        Comparte recursos útiles y ayuda a otras mujeres a encontrar apoyo.
      </p>
    </div>
  </div>

  <!-- Copyright -->
  <div class="border-t border-gray-700 text-center text-sm py-6 text-gray-400">
    <div class="max-w-6xl mx-auto px-6">
      <p class="mb-2">© {year} Entrelazadas, no estamos solas A.C. Todos los derechos reservados.</p>
      <p class="text-xs">Una organización comprometida con erradicar la violencia de género en México.</p>
    </div>
  </div>
</footer>


</div>