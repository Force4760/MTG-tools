<script>
  import { pannable } from "../logic/pannable.js";
  export let size;
  export let left = 100;
  export let value = 50;
  export let label = "Starting Life: ";

  function handlePanMove(event) {
    left += event.detail.dx;
    if (left < 0) {
      left = 0;
    } else if (left > size - 32) {
      left = size - 32;
    }
  }
</script>

<div class="out">
  <p>{label}{value}</p>
  <div
    class="neumorphic-slider"
    bind:clientWidth={size}
    use:pannable
    on:panmove={handlePanMove}
  >
    <div class="neumorphic-slider__line" style="width:{left + 32}px" />
  </div>
</div>

<style>
  .out {
    cursor: pointer;
    display: flex;
    flex-direction: column;
    margin: auto;
    width: 90%;
    max-width: 450px;
    margin-top: 2rem;
  }
  .neumorphic-slider {
    position: relative;
    width: 100%;
    max-width: 450px;
    margin: auto;
    margin-top: 0.5rem;
    height: 2rem;
    background-color: var(--back-color);
    border-radius: 25px;
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
    background: rgba(10, 10, 10, 0.05);
    overflow: hidden;
  }

  .neumorphic-slider__line {
    position: absolute;
    background: #3579c7;
    border-radius: 25px;
    top: 50%;
    height: 100%;
    transform: translateY(-50%);
    box-shadow: 3px 3px 10px 3px var(--bottom-shadow);
  }
  p {
    margin: auto;
    font-size: larger;
    text-shadow: -10px -10px 10px 3px var(--top-shadow),
      10px 10px 10px 3px var(--bottom-shadow);
  }
</style>
