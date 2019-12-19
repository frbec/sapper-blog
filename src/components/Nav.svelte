<script>
  export let segment;
</script>

<style>
  nav {
    border-bottom: 1px solid rgba(12, 160, 86, 0.2);
    font-weight: 300;
    padding: 0 1em;
  }

  ul {
    margin: 0;
    padding: 0;
  }

  /* clearfix */
  ul::after {
    content: "";
    display: block;
    clear: both;
  }

  li {
    display: block;
    float: left;
  }

  .selected {
    position: relative;
    display: inline-block;
  }

  .selected::after {
    position: absolute;
    content: "";
    width: calc(100% - 2em);
    height: 2px;
    background-color: rgb(12, 160, 86);
    display: block;
    bottom: -1px;
  }

  a {
    text-decoration: none;
    padding: 1em 1em;
    display: block;
  }
</style>

<nav>
  <ul>
    <li>
      <a class:selected={segment === undefined} href=".">Startsida</a>
    </li>
    <!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
    <li>
      <a rel="prefetch" class:selected={segment === 'blog'} href="blog">
        Inlägg
      </a>
    </li>
  </ul>
</nav>
