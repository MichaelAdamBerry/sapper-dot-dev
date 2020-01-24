<script>
  export let d;
  let sample = {
    title: "sample title",
    description: "here is a description. It's about 10 words lone",
    tags: ["one", "two", "three"],
    siteUrl: "",
    gitHubUrl: ""
  };
</script>

<style>
  .card {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
    width: 295px;
    height: 185px;
    min-height: 185px;
    color: var(--dk-blu);
    margin: auto;
    /* border: solid; */
    background-color: var(--wht);
    box-shadow: 0px 0px 13px #0009;
  }

  .title-circle {
    grid-row: 1/6;
    grid-column: 1/4;
    width: 185px;
    height: 185px;
    border-radius: 50%;
    background: linear-gradient(311deg, var(--lt-ble), var(--dk-blu) 75%);
    color: var(--wht);
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
    font-size: 25px;
    line-height: 35px;
  }

  .text-circle {
    grid-row: 1/6;
    grid-column: 3/7;
    background-color: var(--wht);

    border-radius: 50%;
  }

  .lower-bg {
    grid-row: 4/6;
    grid-column: 7/5;
    background-color: var(--lt-ble);
  }

  .upper-bg {
    grid-row: 1/4;
    grid-column: 1/3;
    background-color: var(--dk-blu);
    height: 95%;
  }

  .description {
    grid-row: 1/4;
    grid-column: 4/7;
    padding-left: 40px;
    padding-right: 1rem;
    padding-top: 1rem;
  }

  .description p {
    font-size: 11px;
    line-height: 14px;
    margin: 0;
    text-align: center;
  }

  .btns {
    grid-row: 5/6;
    grid-column: 4/6;
    transform: translate(26px, -21px);
    display: flex;
    justify-content: space-around;
  }

  .btn-circ {
    background-color: var(--dk-blu);
    width: 40px;
    min-height: 40px;
    height: 40px;
    border-radius: 50%;
  }

  .launch svg {
    fill: var(--wht);
    transform: translate(7px, 7px);
  }

  .code svg {
    fill: var(--wht);
    transform: scale(1.2) translate(6px, 6px);
  }

  h2 {
    margin: 0;
    font-size: 1.6rem;
  }
</style>

<div class="card">

  <div class="upper-bg" />
  <div class="lower-bg" />
  <div class="text-circle" />
  <div class="description">
    <p>{d.description}</p>
  </div>
  <div class="btns">
    <a href={d.siteUrl === null ? d.gitHubUrl : d.siteUrl}>
      <div class="btn-circ launch">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24">
          <path d="M0 0h24v24H0z" fill="none" />
          <path
            d="M19 19H5V5h7V3H5c-1.11 0-2 .9-2 2v14c0 1.1.89 2 2 2h14c1.1 0 2-.9
            2-2v-7h-2v7zM14 3v2h3.59l-9.83 9.83 1.41 1.41L19 6.41V10h2V3h-7z" />
        </svg>
      </div>
    </a>
    <a href={d.gitHubUrl}>

      <div class="btn-circ code">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24">
          <path d="M0 0h24v24H0z" fill="none" />
          <path
            d="M7.77 6.76L6.23 5.48.82 12l5.41 6.52 1.54-1.28L3.42
            12l4.35-5.24zM7 13h2v-2H7v2zm10-2h-2v2h2v-2zm-6
            2h2v-2h-2v2zm6.77-7.52l-1.54 1.28L20.58 12l-4.35 5.24 1.54
            1.28L23.18 12l-5.41-6.52z" />
        </svg>
      </div>
    </a>
  </div>
  <div class="title-circle">
    <h2>{d.title}</h2>
  </div>

</div>
