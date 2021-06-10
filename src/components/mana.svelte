<script>
  import ManaS from "./manasymbols.svelte";
  import { slide } from "svelte/transition";
  export let width = "10rem";
  export let mwidth = "50%";
  export let height = "10rem";
  export let manasymbol = "S";
  function change(variable, delta) {
    let final = variable + delta;
    if (final < 0) {
      return 0;
    } else {
      return final;
    }
  }

  export let result = 0;
</script>

<div
  transition:slide={{ duration: 300 }}
  class="out"
  style="width:{width};height:{height};max-width:{mwidth}"
>
  <ManaS color={manasymbol} />
  <div class="up" on:click={() => (result = change(result, 1))} />
  <p class="down" on:click={() => (result = change(result, -1))} />
  <p class="result">{result}</p>
</div>

<style>
  .out {
    position: relative;

    margin: 2rem auto;
    margin-bottom: 0;
    vertical-align: middle;
    text-align: center;
    border-radius: 25px;
    box-shadow: -3px -3px 6px 3px var(--top-shadow),
      3px 3px 6px 3px var(--bottom-shadow);
  }
  .up,
  .down {
    left: 0%;
    height: 50%;
    width: 100%;
    position: absolute;
    transition: ease-in 0.2s;
  }
  .up {
    top: 0%;
    border-top-left-radius: 25px;
    border-top-right-radius: 25px;
  }
  .down {
    top: 40%;
    border-bottom-left-radius: 25px;
    border-bottom-right-radius: 25px;
  }
  .up:hover,
  .down:hover {
    background-color: rgba(10, 10, 10, 0.1);
  }
  .result {
    position: absolute;
    top: 10%;
    left: 50%;
    font-size: 4rem;
    transform: translate(-50%, -50%);
  }
</style>
