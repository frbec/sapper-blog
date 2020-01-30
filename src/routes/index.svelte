<script>
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
</script>

<style>
  h1,
  figure,
  p {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  figure {
    margin: 0 0 1em 0;
  }

  img {
    width: 100%;
    max-width: 400px;
    margin: 0 0 1em 0;
  }

  p {
    margin: 1em auto;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }
</style>

<svelte:head>
  <title>Sapper project template</title>
  <script src="https://identity.netlify.com/v1/netlify-identity-widget.js">

  </script>
</svelte:head>

<h1>Bloggy blog</h1>

<figure>
  <img alt="Borat" src="great-success.png" />
  <figcaption>HIGH FIVE!</figcaption>
</figure>

<p>
  <strong>This is a little blog of mine. I hope you feel welcome</strong>
</p>
<p>Here are some links to me on various other websites:</p>
<ul>
  <li>
    <a href="https://twitter.com/frbec" rel="me">@frbec on Twitter</a>
  </li>
  <li>
    <a href="https://github.com/frbec/" rel="me">frbec on GitHub</a>
  </li>
  <li>
    <a href="https://www.facebook.com/frbec" rel="me">frbec on Facebook</a>
  </li>
  <li>
    <a href="https://www.instagram.com/frbec/" rel="me">frbec on Instagram</a>
  </li>
</ul>
