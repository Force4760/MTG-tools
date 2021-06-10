<script>
  import { slide } from "svelte/transition";
  export let checks = ["name", true, true, true, true];
  import TextBox from "./TextBox.svelte";
  import Toggle from "./Toggle.svelte";
</script>

<div class="card" tabindex="0" transition:slide={{ duration: 300 }}>
  <TextBox bind:value={checks[0]} />

  <div class="grid">
    <div class="w">
      <Toggle bind:value={checks[1]} label="Poison" />
    </div>

    <div class="w">
      <Toggle bind:value={checks[2]} label="Energy" />
    </div>
    <div class="w">
      <Toggle bind:value={checks[3]} label="Experience" />
    </div>
    <div class="w">
      <Toggle bind:value={checks[4]} label="Tax" />
    </div>
  </div>
</div>

<style>
  .card {
    display: flex;
    flex-direction: column;
    padding: 8px;
    margin-left: 2rem;
    margin-right: 2rem;
    margin-top: 2rem;
    width: 90%;
    max-width: 450px;
    border-radius: 25px;
    background: rgba(10, 10, 10, 0.05);
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
    transform: 2s;
  }

  .grid {
    color: var(--text-main);
    display: flex;
    width: 90%;
    margin: auto;
    height: 100%;
    justify-content: space-evenly;
    align-items: center;
    flex-wrap: wrap;
  }
  .w {
    width: 50%;
  }
</style>
