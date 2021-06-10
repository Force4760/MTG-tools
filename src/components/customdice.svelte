<script>
  import Text from "./TextBoxN.svelte";
  export let width = "10rem";
  export let height = "10rem";
  export let number = 4;
  function random() {
    if (number > 0) {
      return Math.floor(Math.random() * number + 1);
    } else {
      return Math.floor(Math.random() * number);
    }
  }

  let result = number;
</script>

<div class="out" style="width:{width};height:{height}">
  <div
    class="in"
    style="width:{width};height:{height}"
    on:click={() => {
      result = random();
    }}
  >
    <p class="result">{result}</p>
  </div>
  <div class="text">
    <Text bind:value={number} />
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
</style>
