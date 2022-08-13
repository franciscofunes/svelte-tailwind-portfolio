<script>
	import EyeIcon from './icons/eye-icon.svelte';

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
					class="btn btn-primary shadow hover:opacity-100 duration-300 active:opacity-50 focus:outline-none focus:ring focus:ring-violet-300"
					src={`/projects/${slug}`}
				>
					<EyeIcon />
					<span class="m-2">See</span>
				</button>
			</div>
		</div>
	</a>
</div>
