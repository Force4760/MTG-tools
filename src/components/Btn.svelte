<script>
  export let label = " +";
  export let fun;
  export let font = "3rem";
  export let width = "90%";
  export let marginTop = "2rem";
  export let margin = "auto";
</script>

<div
  class="card"
  tabindex="0"
  on:click={fun}
  style="font-size:{font}; width:{width}; margin:{margin};margin-top:{marginTop}"
>
  <p>{label}</p>
</div>

<style>
  .card {
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    max-height: 3rem;
    max-width: 450px;
    border-radius: 25px;
    background: rgba(10, 10, 10, 0.05);
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
  }
  .card:active {
    box-shadow: inset -3px -3px 6px 3px var(--top-shadow),
      inset 3px 3px 6px 3px var(--bottom-shadow);
    background: rgba(10, 10, 10, 0.05);
  }
  p {
    text-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
    transform: translateX(2px);
  }
</style>
