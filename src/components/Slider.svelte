<script>
  export let value = 50;
  export let label = "Starting Life: ";
</script>

<div class="out">
  <p>{label}{value}</p>
  <input type="range" class="slider" min="10" max="60" bind:value />
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
  .slider {
    -webkit-appearance: none;
    margin: auto;
    margin-top: 1rem;
    width: 100%;
    max-width: 450px;
    height: 2rem;
    background-color: var(--back-color);
    border-radius: 25px;
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
    background: rgba(10, 10, 10, 0.05);
    overflow: hidden;
    outline: none;
    border: none;
  }

  .slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    background: #3579c7;
    color: #3579c7;
    height: 2rem;
    width: 2rem;
    border-radius: 25px;
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
  }

  p {
    margin: auto;
    font-size: larger;
    text-shadow: -10px -10px 10px 3px var(--top-shadow),
      10px 10px 10px 3px var(--bottom-shadow);
  }
</style>
