<script context="module">
	export function preload({ params, query }) {
		return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
	}
</script>

<script>
	export let posts;
</script>

<style>

</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<h1>Latest Stories</h1>

<div>
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<div>
			<h2><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></h2>
			{#if post.description}
			<p>{post.description}</p>
			{/if}
		</div>
	{/each}
</div>