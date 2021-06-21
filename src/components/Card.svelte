<script>
  import Toggle from "./Toggle2.svelte";
  import { slide } from "svelte/transition";
  export let values = {};
  let index = 0;

  function changeValue(value, delta) {
    let final = value + delta;
    return final;
  }
  function changeValueMin(value, delta, min) {
    let final = value + delta;
    if (final >= min) {
      return final;
    } else {
      return min;
    }
  }
  function changeValueWrap(value, delta, max, min) {
    let final = value + delta;
    if (final < min) {
      return max;
    } else if (final > max) {
      return min;
    } else {
      return final;
    }
  }

  function keys(e) {
    switch (e.keyCode) {
      case 37:
        index = changeValueWrap(index, -1, values.props.length - 1, 0);
        break;
      case 38:
        values.props[index][1] = changeValue(values.props[index][1], 1);
        break;
      case 39:
        index = changeValueWrap(index, 1, values.props.length - 1, 0);
        break;
      case 40:
        values.props[index][1] = changeValueMin(values.props[index][1], -1, 0);
        break;
    }
  }
</script>

<div
  class="card"
  tabindex="0"
  on:keydown={keys}
  transition:slide={{ duration: 300 }}
>
  <p class="name">{values.name}</p>
  <img src={values.props[index][0]} alt="type of the value" />
  <div class="value">{values.props[index][1]}</div>
  {#if values.monarch}
    <div class=" light monarch" />
  {/if}
  <div
    class="add change"
    on:click={() =>
      (values.props[index][1] = changeValue(values.props[index][1], 1))}
  />
  <div
    class="minus change"
    on:click={() =>
      (values.props[index][1] = changeValueMin(values.props[index][1], -1, 0))}
  />

  <div
    class="prev change"
    on:click={() =>
      (index = changeValueWrap(index, -1, values.props.length - 1, 0))}
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      ><path
        fill="rgb(200, 200, 200)"
        d="M5 3l3.057-3 11.943 12-11.943 12-3.057-3 9-9z"
      /></svg
    >
  </div>
  <div
    class="next change"
    on:click={() =>
      (index = changeValueWrap(index, 1, values.props.length - 1, 0))}
  >
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="24"
      height="24"
      viewBox="0 0 24 24"
      ><path
        fill="rgb(200, 200, 200)"
        d="M5 3l3.057-3 11.943 12-11.943 12-3.057-3 9-9z"
      /></svg
    >
  </div>
  <div class="toggle">
    <Toggle label="Monarch" size="0.85rem" bind:value={values.monarch} />
  </div>
</div>

<style>
  .light {
    position: absolute;
    left: 0;
    width: 100%;
    height: 10px;
    filter: blur(5px);
    opacity: 0.8;
    transition: 1s linear;
    background: transparent;
  }
  .monarch {
    top: 0;
    background: linear-gradient(
      to bottom,
      rgba(229, 17, 21, 1) 0%,
      rgb(255, 30, 30) 30%,
      rgb(255, 60, 60) 47%,
      rgb(255, 30, 30) 71%,
      rgba(229, 17, 21, 1) 100%
    );
  }

  p.name {
    position: absolute;
    top: 5%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 100%;
    z-index: -1;
    text-align: center;
    font-size: 1.5rem;
  }
  img {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0.8);
    width: 55%;
    opacity: 0.1;
    z-index: -2;
  }
  .value {
    z-index: -1;
    font-size: 5rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  .add {
    border-top-left-radius: 25px;
    border-top-right-radius: 25px;
    width: 100%;
    height: 50%;
  }
  .minus {
    border-bottom-left-radius: 25px;
    border-bottom-right-radius: 25px;
    width: 100%;
    height: 50%;
  }

  .card {
    position: relative;
    height: 270px;
    margin-left: 2rem;
    margin-right: 2rem;
    margin-top: 2rem;
    width: 90%;
    max-width: 450px;
    border-radius: 25px;
    background: rgba(10, 10, 10, 0.05);
    box-shadow: -3px -3px 10px 5px var(--top-shadow),
      3px 3px 10px 5px var(--bottom-shadow);
    transform: 2s;
    overflow: hidden;
  }
  .prev {
    position: absolute;
    border-bottom-left-radius: 25px;
    border-top-left-radius: 25px;
    width: 15%;
    height: 100%;
    top: 0%;
    left: 0%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .prev svg {
    transform: scaleX(-1);
  }

  .next {
    position: absolute;
    border-bottom-right-radius: 25px;
    border-top-right-radius: 25px;
    top: 0%;
    right: 0%;
    width: 15%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .change {
    transition: ease-in 0.2s;

    color: var(--text-main);
  }
  .change:active {
    background-color: rgba(10, 10, 10, 0.1);
  }

  .toggle {
    position: absolute;
    bottom: 2%;
    left: 4%;
    z-index: 10;
    display: flex;

    justify-content: space-between;
  }

  @media (max-width: 600px) {
    .next,
    .prev {
      width: 20%;
    }
  }
</style>
