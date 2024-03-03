<script context="module">
      export function preload({ params, query }) {
        return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
          return { posts };
        });
      }
    </script>
<script>
  import { onMount } from "svelte";
  import _ from "lodash";
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

  @media (min-width: 600px) {
    h1 {
      font-size: 3em;
    }
  }
</style>

<svelte:head>
  <title>Fredrik Beckius | Connect</title>
  <!-- Import netlify identity check -->
  <script src="https://identity.netlify.com/v1/netlify-identity-widget.js">

  </script>
</svelte:head>

<h1>Work</h1>

{#each _.orderBy(posts, ['date'], ['desc']) as post (post.slug)}
  <PostListing {post} />
{/each}