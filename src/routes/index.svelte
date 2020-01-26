<script>
  import { onMount, onDestroy } from "svelte";
  import LandingSVG from "../components/LandingSVG.svelte";

  //TODO active animation should automatically loop though the three categories
  // When a word is hovered over it should cancel this loop or restart this loop
  $: webDevActive = false;
  $: dataActive = false;
  $: uiActive = false;
  $: cancelAnimations = false;
  //starting animation to fire.
  let next = "uiActive";
  let intervalId;
  let startInterval;
  let clearInterval;

  function clearAll() {
    cancelAnimations = true;
    dataActive = false;
    uiActive = false;
    webDevActive = false;
  }

  function updateAnimation(activeAnimation) {
    switch (activeAnimation) {
      case "dataActive":
        dataActive = true;
        next = "webDevActive";
        break;
      case "uiActive":
        uiActive = true;

        next = "dataActive";
        break;
      case "webDevActive":
        webDevActive = true;
        next = "uiActive";
        break;
      default:
        console.warn("switch did not return a true case");
    }
  }

  //Isolate window to run in client only by putting code in onMount and onDestroy methods

  onMount(() => {
    //startInterval creates a new interval instance
    //and assigns it's id to equal interval id
    //and defines our clearInterval function
    // startInterval will be called when user resets or stops the animation
    startInterval = () => {
      intervalId = window.setInterval(() => {
        clearAll();
        updateAnimation(next);
        cancelAnimations = false;
      }, 2500);
      clearInterval = () => window.clearInterval(intervalId);
    };
    startInterval();
  });

  onDestroy(() => {
    window.clearInterval(intervalId);
  });
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
    <p>
      <span
        style={webDevActive && 'background-color: var(--yl)'}
        on:mouseenter={() => {
          clearInterval();
          cancelAnimations = false;
          webDevActive = true;
        }}
        on:mouseleave={() => {
          startInterval();
          webDevActive = false;
          cancelAnimations = true;
        }}>
        Web Development
      </span>
      •
      <span
        style={dataActive && 'background-color: var(--yl)'}
        on:mouseenter={() => {
          clearInterval();
          cancelAnimations = false;
          dataActive = true;
        }}
        on:mouseleave={() => {
          startInterval();
          dataActive = false;
          cancelAnimations = true;
        }}>
        Data Visualization
      </span>
      •
      <span
        style={uiActive && 'background-color: var(--yl)'}
        on:mouseenter={() => {
          clearInterval();
          cancelAnimations = false;
          uiActive = true;
        }}
        on:mouseleave={() => {
          startInterval();
          uiActive = false;
          cancelAnimations = true;
        }}>
        Interactive UIs
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
