<script>
	export let url = '';
	export let name = '';
	export let slug = '';
	export let description = '';
</script>

<!-- <div class="relative group card shadow-2xl col-span-2 m-2">
	<img src={url} alt={name} class="object-cover h-full " />
	<a href={`/projects/${slug}`}>
		<div
			class="absolute bottom-0 left-0 right-0 lg:opacity-0 group-hover:opacity-100 bg-primary p-4 duration-300 text-primary-content"
		>
			<h2 class="font-bold lg:text-xl">{name}</h2>
			<p class="text-sm lg:text-xl">
				{description.slice(0, 80)}...
			</p>
		</div>
	</a>
</div> -->

<div class="card card-compact  shadow-xl ">
	<figure><img src={url} alt={name} /></figure>
	<a href={`/projects/${slug}`}>
		<div class="card-body ">
			<h2 class="font-bold lg:text-xl">{name}</h2>
			<p class="text-sm lg:text-xl">
				{description.slice(0, 80)}...
			</p>
			<div class="card-actions justify-end">
				<button
					class="btn btn-primary shadow hover:opacity-100 duration-300 active:bg-violet-700 focus:outline-none focus:ring focus:ring-violet-300"
					src={`/projects/${slug}`}
				>
					<svg
						x-show="!isTabsActive"
						class="w-6 h-6 text-white animate-ping"
						fill="none"
						stroke="currentColor"
						viewBox="0 0 24 24"
						xmlns="http://www.w3.org/2000/svg"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"
						/>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"
						/>
					</svg>
					<span class="m-2">Ver</span>
				</button>
			</div>
		</div>
	</a>
</div>
