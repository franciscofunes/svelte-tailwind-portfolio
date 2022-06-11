<script context="module">
	import ProjectCard from '$lib/components/project-card.svelte';
	import { client } from '$lib/graphql-client';
	import { authorsQuery, projectsQuery } from '$lib/graphql-queries';

	export const load = async () => {
		const [authorReq, projectsReq] = await Promise.all([
			client.request(authorsQuery),
			client.request(projectsQuery)
		]);
		const { authors } = authorReq;
		const { projects } = projectsReq;

		return {
			props: {
				projects,
				authors
			}
		};
	};
</script>

<script>
	export let projects;
	export let authors;
</script>

<svelte:head>
	<title>Portfolio - Francisco Funes</title>
</svelte:head>

<h1 class="font-bold text-center mb-10 text-5xl 1 m-5">
	Bievenidos a mi <span
		class="before:block before:absolute before:-inset-1 before:-skew-y-3 before:bg-gradient-to-r from-purple-500 via-white-500 to-pink-500 relative inline-block mt-4"
	>
		<span class="relative text-white ">Portfolio</span>
	</span>
</h1>

{#each authors as { name, intro, picture: { url } }}
	<div class="flex mb-5 items-start">
		<div class="mr-3">
			<h2
				class="text-2xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-gray-500 via-white-500 to-black-500"
			>
				{name}
			</h2>
			<p class="text-xl mb-2">{intro}</p>
		</div>
		<img class="mask mask-squircle h-40 saturate-60 " src={url} alt={name} />
	</div>
{/each}

<div
	class="p-10 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-5"
>
	<article class="prose lg:prose-xl">
		<h1>
			Mis <span
				class="before:block before:absolute before:-inset-1 before:-skew-y-3 before:bg-gray-500 relative inline-block"
			>
				<span class="relative text-white ">proyectos</span>
			</span> recientes
		</h1>
	</article>

	{#each projects as { name, slug, description, image }}
		<ProjectCard {name} {description} url={image[0].url} {slug} />
	{/each}
</div>
