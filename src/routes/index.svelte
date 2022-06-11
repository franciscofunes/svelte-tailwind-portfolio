<script context="module">
	import ProjectCard from '$lib/components/project-card.svelte';
	import { client } from '$lib/graphql-client';
	import { gql } from 'graphql-request';

	export const load = async () => {
		const query = gql`
			query GetProjects {
				projects {
					name
					slug
					description
					tags
					demo
					sourceCode
					image {
						url
					}
				}
			}
		`;
		const { projects } = await client.request(query);

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
