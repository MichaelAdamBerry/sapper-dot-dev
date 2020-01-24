<script>
  export let segment;
</script>

<style>
  nav {
    width: 50%;
    margin-left: 50%;
  }

  ul {
    margin: 0;
    padding: 0;
  }

  /* clearfix */
  ul::after {
    content: "";
    display: block;
    /* clear: both; */
  }

  li {
    display: block;
  }

  .selected {
    position: relative;
    display: inline-block;
    font-weight: bold;
  }

  .selected::after {
    position: absolute;
    content: "";
    width: calc(100% - 1rem);
    height: 2px;
    background-color: var(--almost-black);
    display: block;
    bottom: -1px;
  }

  a {
    text-decoration: none;
    padding: 0rem 0.5rem;
    display: block;
    font-family: var(--heading-font);
    font-size: 38px;
    color: var(--almost-black);
    /* opacity: 0.99; */
  }
</style>

<nav>
  <ul>
    <li>
      <a class:selected={segment === undefined} href=".">home</a>
    </li>
    <li>
      <a class:selected={segment === 'about'} href="about">about</a>
    </li>

    <!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
    <li>
      <a rel="prefetch" class:selected={segment === 'blog'} href="blog">blog</a>
    </li>
  </ul>
</nav>

