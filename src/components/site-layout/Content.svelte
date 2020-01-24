<script>
  import Nav from "../Nav.svelte";
  export let segment;
</script>

<style>
  .with-sidebar {
    overflow: hidden;
    width: 100%;
    height: calc(100vh - var(--footer-height) - var(--header-height));
    min-height: calc(100vh - var(--footer-height) - var(--header-height));
  }

  .wrapper {
    width: 100%;
    height: 100%;
  }

  .with-sidebar > * {
    display: flex;
    flex-wrap: wrap;
  }

  .with-sidebar > * > * {
    flex-basis: 350px;
    flex-grow: 1;
  }

  .with-sidebar > * > :last-child {
    flex-basis: 0;
    flex-grow: 999;
    min-width: calc(62% - 1rem);
  }
  .sidebar {
    background-color: var(--almost-white);
  }

  .content {
    border-left: solid;
    background-color: var(--almost-white);
    width: 100%;
  }

  .clipped {
    position: relative;
    width: 50%;
    height: 100%;
    margin-left: 70%;
    background-color: var(--almost-black);

    clip-path: url(#swoop);
  }
</style>

<div class="with-sidebar">
  <div class="wrapper">
    <!-- intermediary wrapper -->
    <div class="sidebar">
      <Nav {segment} />

      <!-- sidebar -->
    </div>

    <div class="content">
      <!-- non-sidebar -->
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
      <div class="clipped" />
    </div>
  </div>
</div>

