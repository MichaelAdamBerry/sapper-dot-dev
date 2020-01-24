<script>
  import Header from "../components/Header.svelte";

  export let segment;
</script>

<style>
  .layout {
    display: flex;
    flex-direction: column;
    min-height: 100%;
    min-height: 100vh;
  }

  main {
    flex: 1;
    position: relative;
    margin: 0 auto;
    max-width: 1400px;
    /* background-color: white; */
    padding: 1em 2em;
    box-sizing: border-box;
    width: 100%;
    display: flex;
    flex-direction: column;
  }

  footer {
    color: #aaa;
    font-size: 16px;
    font-family: Rubik, sans-serif;
    max-width: 1400px;

    text-align: center;
    width: 100%;
    background-color: var(--dk-blu);
    z-index: 2;
  }

  .swoop-container {
    position: relative;
    height: 0px;
  }

  .bg-swoop {
    position: fixed;
    top: 0;
    right: 0;
    height: 100vh;
    width: 40vw;
    background-color: var(--wht);
    transform: translate(40%, 0);
  }

  .clipped {
    background-color: var(--dk-blu);
    clip-path: url(#swoop);
    width: 100%;
    height: 100%;
  }
</style>

<div class="swoop-container">
  <svg width="0" height="0">
    <defs>
      <clipPath
        id="swoop"
        clipPathUnits="objectBoundingBox"
        transform="scale(.01)">
        <path
          d="M.1,99.9c19.9.2,39.9,0,59.8.1a14.1,14.1,0,0,0,.1-2.1V0a152,152,0,0,1-4.1,29.3c-2.1,8.1-4.3,16.9-10,26.6a108.7,108.7,0,0,1-8.8,12.2c-4,5-8.9,11.3-16.4,17.7A93,93,0,0,1,.1,99.9Z" />
      </clipPath>
    </defs>
  </svg>
  <div class="bg-swoop">
    <div class="clipped" />
  </div>

</div>

<div class="layout">
  <Header {segment} />

  <main>
    <slot />
  </main>

  <footer>
    <span>
      &copy; {new Date().getFullYear()} AdamBerry.dev Powered by
      <a href="https://svelte.dev">Svelte</a>
      and
      <a href="https://sapper.svelte.dev" target="_blank">Sapper</a>
      <!-- . Template by
      <a href="https://www.twitter.com/Charca" target="_blank">Maxi Ferreira</a> -->
      .
    </span>
  </footer>
</div>
