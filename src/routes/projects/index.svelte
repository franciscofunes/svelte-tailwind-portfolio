<script context="module">
	import ProjectCard from '$lib/components/project-card.svelte';
	import { client } from '$lib/graphql-client';
	import { projectsQuery } from '$lib/graphql-queries';

	export const load = async () => {
		const { projects } = await client.request(projectsQuery);

		return {
			props: {
				projects
			}
		};
	};
</script>

<script>
	export let projects;
</script>

<svelte:head>
	<title>My projects</title>
</svelte:head>

<div
	class="p-10 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-3 gap-5"
>
	<article class="prose mb-5 mt-0">
		<h1>
			My last <span
				class="before:block before:absolute before:-inset-1 before:-skew-y-3 before:bg-gray-500 relative inline-block"
			>
				<span class="relative text-white ">recent</span>
			</span> projects
		</h1>
	</article>

	{#each projects as { name, slug, description, image }}
		<ProjectCard {name} {description} url={image[0].url} {slug} />
	{/each}
</div>
