<script>
  import { slide } from "svelte/transition";
  export let width = "10rem";
  export let height = "10rem";
  export let label = "D 4";
  export let number = 4;
  function random() {
    return Math.floor(Math.random() * number + 1);
  }

  let result = number;
</script>

<div
  transition:slide={{ duration: 300 }}
  class="out"
  style="width:{width};height:{height}"
  on:click={() => {
    result = random();
  }}
>
  <p class="result">{result}</p>
  <p class="label">{label}</p>
</div>

<style>
  .out {
    position: relative;
    max-width: 50%;
    margin: 2rem auto;
    margin-bottom: 0;
    vertical-align: middle;
    text-align: center;
    border-radius: 25px;
    box-shadow: -3px -3px 6px 3px var(--top-shadow),
      3px 3px 6px 3px var(--bottom-shadow);
  }
  .result {
    position: absolute;
    top: 10%;
    left: 50%;
    font-size: 4rem;
    transform: translate(-50%, -50%);
  }
  .label {
    font-size: 1.5rem;
    position: absolute;

    left: 50%;

    transform: translate(-50%, -50%);
  }
  .out:active {
    box-shadow: inset -3px -3px 6px 3px var(--top-shadow),
      inset 3px 3px 6px 3px var(--bottom-shadow);
  }
</style>
