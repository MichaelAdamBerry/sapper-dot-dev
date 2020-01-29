<script>
  import LandingSVG from "../components/LandingSVG.svelte";
  let webDevActive = false;
  let dataActive = false;
  let uiActive = false;
  let cancelAnimations = false;
</script>

<style>
  .home-container {
    align-items: center;
    display: flex;
    flex: 1;
    justify-content: center;
    margin: 2em 0;
    min-height: 400px;
  }

  .home-copy {
    flex: 1;
  }

  h1 {
    font-weight: 700;
    margin-bottom: 0;
    font-size: 7em;
    cursor: none;
  }

  p {
    font-size: 1.4em;
    line-height: 1.4;
    margin-top: 0.5rem;
  }

  .img {
    width: 100%;
    max-width: 400px;
  }

  @media (max-width: 1020px) {
    p {
      font-size: 1.2em;
    }

    .img {
      max-width: 300px;
    }
  }

  @media (max-width: 800px) {
    .home-container {
      flex-direction: column;
    }

    .home-copy {
      flex: 0;
      padding-bottom: 2em;
      text-align: center;
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 3em;
      }
    }
  }
</style>

<svelte:head>
  <title>Adam Berry | Web Development</title>
</svelte:head>

<div class="home-container">
  <div class="home-copy">
    <h1>AdamBerry.dev</h1>
    <p
      style={webDevActive ? 'cursor: url(./tri-cursor.png), auto' : uiActive ? 'cursor: url(./sq-cursor.png), auto' : 'cursor: url(./circ-cursor.png), auto'}>
      <span
        style={webDevActive && 'background-color: var(--yl);'}
        on:mouseenter={() => {
          cancelAnimations = false;
          webDevActive = true;
        }}
        on:mouseleave={() => {
          webDevActive = false;
          cancelAnimations = true;
        }}>
        Web Development
      </span>

      <span
        style={dataActive && 'background-color: var(--yl)'}
        on:mouseenter={() => {
          cancelAnimations = false;
          dataActive = true;
        }}
        on:mouseleave={() => {
          dataActive = false;
          cancelAnimations = true;
        }}>
        • Data Visualization
      </span>
      <span
        style={uiActive && 'background-color: var(--yl)'}
        on:mouseenter={() => {
          cancelAnimations = false;
          uiActive = true;
        }}
        on:mouseleave={() => {
          uiActive = false;
          cancelAnimations = true;
        }}>
        • Interactive UIs
      </span>
    </p>
  </div>
  <div class="img">
    <LandingSVG {webDevActive} {cancelAnimations} {dataActive} {uiActive} />

  </div>

  <!-- <figure>
    <img alt="Person typing on laptop" src="bubbles-1.svg" />
    <!-- <figcaption>
      Illustration thanks to
      <a href="https://undraw.co" target="_blank">Undraw</a>
    </figcaption> -->
  <!-- </figure> -->
</div>
