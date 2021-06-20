<script>
  export let value;
  export let label;
  export let size = "1rem";

  function handleChange() {
    value = !value;
  }
</script>

<label class="label">
  <input
    class="toggle-state"
    type="checkbox"
    name="check"
    checked={value}
    on:change={handleChange}
  />
  <div class="toggle">
    <div class="indicator" />
  </div>
  <div class="label-text" style="font-size: {size};">{label}</div>
</label>

<style>
  .label {
    display: inline-flex;
    align-items: center;
    cursor: pointer;
    color: var(--text-main);

    margin: 1rem;
  }

  .label-text {
    margin-left: 16px;
    font-size: 1rem;
  }

  .toggle {
    isolation: isolate;
    position: relative;
    height: 30px;
    width: 30px;
    border-radius: 15px;
    overflow: hidden;
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
  }

  .toggle-state {
    display: none;
  }

  .indicator {
    height: 100%;
    width: 100%;
    background: #3579c7;
    border-radius: 15px;
    transition: 0.3s linear;
    opacity: 0;
  }

  .toggle-state:checked ~ .toggle .indicator {
    opacity: 1;
  }
</style>
