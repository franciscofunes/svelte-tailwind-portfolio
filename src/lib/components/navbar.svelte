<script>
	import HamburgerIcon from './icons/hamburger-icon.svelte';
	import ThemeSelect from './theme-select.svelte';
	import LogoIcon from './icons/logo-icon.svelte';
</script>

<div class="navbar mb-5 shadow-lg bg-neutral text-neutral-content sticky top-0 z-10">
	<div class="flex-1 ml-1">
		<a class="" href="/"><LogoIcon /></a>
	</div>

	<div class="dropdown dropdown-left lg:hidden transition transform opacity-100 scale-100">
		<HamburgerIcon />
		<ul tabindex="0" class="bg-neutral rounded-box shadow  mt-7 mr-2 w-40 menu dropdown-content">
			<a class="btn btn-ghost btn-sm rounded-btn" href="/projects">Portfolio </a>
			<a class="btn btn-ghost btn-sm rounded-btn" href="/posts">Blog </a>
			<a class="btn btn-ghost btn-sm rounded-btn" href="/about">About me </a>
		</ul>
	</div>

	<div class="flex-none hidden px-2 mt-4 lg:flex">
		<div class="flex items-stretch">
			<a class="btn btn-ghost btn-sm rounded-btn" href="/projects"> Portfolio </a>
			<a class="btn btn-ghost btn-sm rounded-btn" href="/posts">Blog</a>
			<a class="btn btn-ghost btn-sm rounded-btn" href="/about">About me</a>
			<div class="px-4 mt-1">
				<ThemeSelect />
			</div>
		</div>
	</div>
</div>
