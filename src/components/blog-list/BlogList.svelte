<script>
  import BlogListItem from "./BlogListItem.svelte";
  export let isSideItem;
  let sampleData = [
    {
      title: "title",
      date: "January 2nd, 2020",
      subtitle: "some subtitle goes here",
      tags: ["one", "two", "three"]
    },
    {
      title: "title",
      date: "January 2nd, 2020",
      subtitle: "some subtitle goes here",
      tags: ["one", "two", "three"]
    },
    {
      title: "title",
      date: "January 2nd, 2020",
      subtitle: "some subtitle goes here",
      tags: ["one", "two", "three"]
    },
    {
      title: "title",
      date: "January 2nd, 2020",
      subtitle: "some subtitle goes here",
      tags: ["one", "two", "three"]
    }
  ];

  //sets blog list to be either the first thee items in array or 10
  // TODO deal with pagination for blog indecies above 10;
  let data = isSideItem ? sampleData.slice(0, 3) : sampleData.slice(0, 9);
</script>

<style>
  .blog-list {
    margin-top: 1.5rem;
    overflow: scroll;
  }
  ul {
    list-style: none;
    padding-left: 0;
  }
</style>

<div class="blog-list">
  <ul>
    {#each data as d}
      <BlogListItem {d} />
    {/each}
  </ul>
</div>
