  <script context="module">
      export function preload({ params, query }) {
        return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
          return { posts };
        });
      }
    </script>
<script>
  import { onMount } from "svelte";
  import PostListing from "../components/PostListing.svelte"

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
  export let showSwedish = true;
</script>

<style>
  h1 {
    margin: 0 auto;
  }

  h1 {
    font-size: 2em;
    text-transform: uppercase;
    font-weight: 700;
    margin-bottom: 0.5em;
  }

  label {
    cursor: pointer;
    display: inline-block;
    border: 10px solid rgb(29, 45, 56);
    border-radius: 12px;
    padding: .5em 1em;
    margin-bottom: 1em;
    font-size: 0.9em;
  }

  @media (min-width: 600px) {
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

<label>
<input type="checkbox" bind:checked={showSwedish} aria-checked="true">
Show Swedish posts
</label>

{#each posts as post (post.slug)}
		<!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
    {#if showSwedish || post.language === "en"}
      <PostListing {post} />
    {/if}
	{/each}