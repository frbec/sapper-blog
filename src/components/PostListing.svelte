<script>
  import moment from "moment";

  export let post
</script>

<style>  h2 {
    font-size: 1.6em;
    font-weight: 500;
    margin-bottom: 0.5em;
  }

  h2 a {
      text-decoration: none;
  }

  h4 {
    font-size: 1em;
    font-weight: 400;
    margin-bottom: 0.5em;
  }

  p {
    margin-bottom: 0
  }

  article {
    padding: .5em;
    margin-bottom: 1.5em;
  }

  a:hover {
      text-decoration: underline
  }

  article:last-child {
    margin-bottom: 0;
  }

  .category {
    margin-left: 0.5em;
    color: khaki;
  }</style>

<article>
      <h4>{moment(post.date).format("MMMM D, YYYY")}<span class="category">{post.category}</span></h4>
			<h2><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></h2>
			{#if post.description}
			<p>{post.description}</p>
			{/if}
		</article>