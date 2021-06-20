<script>
  export let value = "";
  export let placeholder = "Name";
  export let max = "20";
  export let margin = "1rem";
</script>

<div class="searchbx" style="margin-top: {margin};margin-bottom:{margin};">
  <div class="field">
    <span class="" aria-hidden="true" />
    <input type="text" {placeholder} maxlength={max} bind:value />
  </div>
</div>

<style>
  .searchbx {
    width: 90%;
    margin: auto;
  }
  .field {
    height: 3rem;
    width: 100%;
    display: flex;
    position: relative;
    background: none;
    color: var(--text-main);
  }
  .field span {
    position: absolute;
    width: 50px;
    line-height: 42px;
    color: var(--text-main);
    background: none;
    left: 14px;
  }
  .field input {
    height: 100%;
    width: 100%;
    padding-left: 2rem;
    font-size: 1.2rem;
    font-weight: 600;
    outline: none;
    border: none;
    color: var(--text-main);
    background: none;
    border-radius: 25px;
    box-shadow: -3px -3px 10px 3px var(--top-shadow),
      3px 3px 10px 3px var(--bottom-shadow);
  }
  .field input::placeholder {
    color: var(--text-second);
  }
  .field input:focus {
    box-shadow: inset -3px -3px 10px 3px var(--top-shadow),
      inset 3px 3px 10px 3px var(--bottom-shadow);
  }
</style>
