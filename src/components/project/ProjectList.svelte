<script>
  import Card from "./Card.svelte";
  import BlogList from "../blog-list/BlogList.svelte";

  let sampleData = ["a", "b,", "c", "d", "e", "d"];

  const projects = [
    // {
    //   title: "",
    //   description: "",
    //   tags: [],
    //   siteUrl: "",
    //   gitHubUrl: ""
    // }
    {
      title: "Trumpcare",
      description:
        "Interactive timeline refuting President Trump's healthcare claims",
      tags: ["interactive-journalism", "politics"],
      siteUrl: "https://preexisting-conditions.now.sh/",
      gitHubUrl:
        "https://github.com/MichaelAdamBerry/trump-preexisting-conditions-lies"
    },
    {
      title: "Eleftable",
      description:
        "Interactive survey of 2020 Democratic candidates for President ",
      tags: [
        "svelte",
        "d3",
        "interactive-journalism",
        "politics",
        "data-visualization"
      ],
      siteUrl: "https://eleftable.now.sh",
      gitHubUrl: "https://github.com/MichaelAdamBerry/electable2020"
    },
    {
      title: "Grateful Data",
      description: "Visualizing 30 years of setlist data of The Grateful Dead",
      tags: [
        "d3",
        "vanillajs",
        "javascript",
        "pop-culture",
        "data-visualization",
        "interactive-journalism"
      ],
      siteUrl: "https://grateful-data.com",
      gitHubUrl: "https://github.com/MichaelAdamBerry/darkstar-project"
    },
    {
      title: "The Obsessionists",
      description: "Pop culture blog built with React and Gatsby.",
      tags: ["blog", "react", "gatsby"],
      siteUrl: null,
      gitHubUrl: "https://github.com/MichaelAdamBerry/the-obsessionists"
    },
    {
      title: "My Reps",
      description:
        "React application to find and connect with elected representatives",
      tags: ["react"],
      siteUrl: "https://myreps20.michaeladamberry3.now.sh/",
      gitHubUrl: "https://github.com/MichaelAdamBerry/my_reps2.0"
    },
    {
      title: "Data Views",
      description: "Front end demo for a data dashboard",
      tags: ["d3", "svg", "canvas"],
      siteUrl: "https://dataviews.netlify.com/",
      gitHubUrl: "https://github.com/MichaelAdamBerry/dashboard"
    },
    {
      title: "Time Peace",
      description: "Gatsby and Shopify e-commerce demo",
      tags: ["react", "gatsby", "e-commerce", "shopify"],
      siteUrl: null,
      gitHubUrl: "https://github.com/MichaelAdamBerry/time-peace"
    }
  ];
</script>

<style>
  .project-list {
    max-width: 900px;
  }

  .project-page-container {
    display: flex;
    justify-content: space-around;
  }

  ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
    padding: 0;
  }

  li {
    width: 50%;
    margin-bottom: 3rem;
  }

  h1 {
    margin-left: 80px;
    margin-bottom: 0.5rem;
  }

  @media (max-width: 1200px) {
    @media (max-width: 700px) {
      li {
        width: 80%;
      }
    }
  }
</style>

<div class="project-page-container">
  <!-- <div class="side-content">
    <h2>Recent Blog Posts</h2>
    <BlogList isSideItem={true} />
  </div> -->
  <div class="project-list">
    <h1>Side Projects</h1>
    <ul>
      {#each projects as d}
        <li>

          <Card {d} />
        </li>
      {/each}
    </ul>

  </div>
</div>
