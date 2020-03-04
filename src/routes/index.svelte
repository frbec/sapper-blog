  <script context="module">
      export function preload({ params, query }) {
        return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
          return { posts };
        });
      }
    </script>
<script>
  import moment from "moment";
  import { onMount } from "svelte";

  onMount(() => {
    if (window.netlifyIdentity) {
      window.netlifyIdentity.on("init", user => {
        if (!user) {
          window.netlifyIdentity.on("login", () => {
            document.location.href = "/admin/";
          });
        }
      });
    }
  });

	export let posts;
</script>

<style>
  h1,
  h2,
  h4,
  p {
    margin: 0 auto;
  }

  h1 {
    font-size: 2em;
    text-transform: uppercase;
    font-weight: 700;
    margin-bottom: 0.5em;
  }

  h2 {
    font-size: 1.6em;
    font-weight: 500;
    margin-bottom: 0.5em;
  }

  h4 {
    font-size: 1em;
    text-transform: uppercase;
    font-weight: 500;
    margin-bottom: 0.5em;
  }

  p {
    margin-bottom: 1em
  }

  article {
    margin-bottom: 2em;
  }

  article:last-child {
    margin-bottom: 0;
  }

  .category {
    margin-left: 0.5em;
    color: blue;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 3em;
    }
  }
</style>

<svelte:head>
  <title>Beckius Blabs</title>
  <!-- Import netlify identity check -->
  <script src="https://identity.netlify.com/v1/netlify-identity-widget.js">

  </script>
</svelte:head>

<h1>Recent Blabbings</h1>

<div>
	{#each posts as post}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
		<article>
      <h4>{moment(post.date).format("MMMM D, YYYY")}<span class="category">{post.category}</span></h4>
			<h2><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></h2>
			{#if post.description}
			<p>{post.description}</p>
			{/if}
		</article>
	{/each}
</div>