<script context="module">
	import { client } from '$lib/graphql-client';
	import { authorsQuery } from '$lib/graphql-queries';
	import { marked } from 'marked';

	export const load = async () => {
		const { authors } = await client.request(authorsQuery);

		return {
			props: {
				authors
			}
		};
	};
</script>

<script>
	export let authors;
	const {
		name,
		intro,
		bio,
		picture: { url }
	} = authors[0];
</script>

<svelte:head>
	<title>My Portfolio project | About {name}</title>
</svelte:head>

<!-- <h1 class="font-bold text-center mb-20 text-5xl">About me</h1> -->

<div class="flex mb-5 items-start">
	<div class="mr-6">
		<h2 class="text-3xl mt-10 mb-2 font-bold tracking-wider">{name}</h2>
		<p class="text-xl  mb-2">{intro}</p>
	</div>

	<img class="mask shadow mask-squircle mt-10 h-40" src={url} alt={name} />
</div>

<article div class="prose prose-lg">
	{@html marked(bio)}
</article>
