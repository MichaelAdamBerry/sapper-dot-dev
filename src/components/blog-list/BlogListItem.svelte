<script>
  export let d;
</script>

<style>
  .blog-item {
    padding: 0;
    width: 90%;
    border-bottom: solid 1px;
    margin-bottom: 1.5rem;
  }

  li,
  h3,
  p,
  span {
    font-family: var(--heading-font);
  }

  p,
  span {
    font-size: 18px;
  }

  span {
    margin-right: 1rem;
  }

  p {
    margin: 0;
  }

  h3 {
    font-size: 30px;
    line-height: 30px;
    margin: 0;
  }
</style>

<li class="blog-item">
  <p class="date">{d.date}</p>
  <h3>{d.title}</h3>
  <p>{d.subtitle}</p>
  <div class="tags">
    {#each d.tags as t}
      <span>{t}</span>
    {/each}
  </div>

</li>
