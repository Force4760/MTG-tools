<script>
  import Text from "./TextBoxN.svelte";
  import { slide, fade } from "svelte/transition";
  export let width = "10rem";
  export let height = "10rem";
  export let number = 4;
  let loading = false;
  function random() {
    if (number > 0) {
      return Math.floor(Math.random() * number + 1);
    } else {
      return Math.floor(Math.random() * number);
    }
  }
  function handleClick() {
    loading = true;
    setTimeout(() => {
      loading = false;
    }, 1000);
    result = random();
  }

  let result = number;
</script>

<div
  class="out scale"
  style="width:{width};height:{height}"
  transition:slide={{ duration: 300 }}
>
  <div class="in" style="width:{width};height:{height}" on:click={handleClick}>
    {#if loading}
      <svg
        width="57"
        height="57"
        viewBox="0 0 57 57"
        xmlns="http://www.w3.org/2000/svg"
        stroke="none"
        transition:slide
      >
        <g fill="none" fill-rule="evenodd">
          <g transform="translate(1 1)" stroke-width="2">
            <circle cx="5" cy="50" r="5">
              <animate
                attributeName="cy"
                begin="0s"
                dur="2.2s"
                values="50;5;50;50"
                calcMode="linear"
                repeatCount="indefinite"
              />
              <animate
                attributeName="cx"
                begin="0s"
                dur="2.2s"
                values="5;27;49;5"
                calcMode="linear"
                repeatCount="indefinite"
              />
            </circle>
            <circle cx="27" cy="5" r="5">
              <animate
                attributeName="cy"
                begin="0s"
                dur="2.2s"
                from="5"
                to="5"
                values="5;50;50;5"
                calcMode="linear"
                repeatCount="indefinite"
              />
              <animate
                attributeName="cx"
                begin="0s"
                dur="2.2s"
                from="27"
                to="27"
                values="27;49;5;27"
                calcMode="linear"
                repeatCount="indefinite"
              />
            </circle>
            <circle cx="49" cy="50" r="5">
              <animate
                attributeName="cy"
                begin="0s"
                dur="2.2s"
                values="50;50;5;50"
                calcMode="linear"
                repeatCount="indefinite"
              />
              <animate
                attributeName="cx"
                from="49"
                to="49"
                begin="0s"
                dur="2.2s"
                values="49;5;27;49"
                calcMode="linear"
                repeatCount="indefinite"
              />
            </circle>
          </g>
        </g>
      </svg>
    {:else}
      <p class="result" transition:fade>{result}</p>
    {/if}
  </div>
  <div class="text">
    <Text bind:value={number} placeholder="---" />
  </div>
</div>

<style>
  .out {
    position: relative;
    max-width: 50%;
    margin: 2rem auto;
    margin-bottom: 0;
  }
  .in {
    position: relative;
    vertical-align: middle;
    text-align: center;
    border-radius: 25px;
    box-shadow: -3px -3px 6px 3px var(--top-shadow),
      3px 3px 6px 3px var(--bottom-shadow);
  }
  .result {
    position: absolute;
    top: 30%;
    left: 50%;
    font-size: 4rem;
    transform: translate(-50%, -50%);
  }

  .in:active {
    box-shadow: inset -3px -3px 6px 3px var(--top-shadow),
      inset 3px 3px 6px 3px var(--bottom-shadow);
  }
  .text {
    position: absolute;
    top: 0%;
  }
  svg {
    position: absolute;
    top: 65%;
    left: 50%;
    font-size: 4rem;
    transform: translate(-50%, -50%);
    stroke: var(--text-main);
  }
  @media (max-width: 365px) {
    .scale {
      transform: scale(0.9);
    }
  }
</style>
