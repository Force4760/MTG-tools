<script>
  export let value;
  export let label;

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
  <div class="label-text">{label}</div>
</label>

<style>
  .label {
    display: inline-flex;
    align-items: center;
    cursor: pointer;
    color: var(--text-main);
    margin-top: 1rem;
    margin-bottom: 1rem;
  }

  .label-text {
    margin-left: 16px;
  }

  .toggle {
    isolation: isolate;
    position: relative;
    height: 30px;
    width: 60px;
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
    width: 200%;
    background: #3579c7;
    border-radius: 15px;
    transform: translate3d(-75%, 0, 0);
    transition: transform 0.4s cubic-bezier(0.85, 0.05, 0.18, 1.35);
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
  }

  .toggle-state:checked ~ .toggle .indicator {
    transform: translate3d(25%, 0, 0);
  }
</style>
