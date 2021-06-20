<script>
  export let value = "";
  export let margin = "1rem";
</script>

<div class="box" style="margin-top: {margin};margin-bottom:{margin};">
  <div class="field">
    <select bind:value>
      <option value="name">Sort by Name</option>
      <option value="released">Sort by Release Date</option>
      <option value="set">Sort by Set/Number</option>
      <option value="rarity">Sort by Rarity</option>
      <option value="color">Sort by Color</option>
      <option value="usd">Sort by USD</option>
      <option value="tix">Sort by TIX</option>
      <option value="eur">Sort by EUR</option>
      <option value="cmc">Sort by CMC</option>
      <option value="power">Sort by Power</option>
      <option value="toughness">Sort by Toughness</option>
      <option value="edhrec">Sort by EDHREC</option>
      <option value="artist">Sort by Artist</option>
    </select>
  </div>
</div>

<style>
  .box {
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

  .field select {
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
  .field select:focus {
    box-shadow: inset -3px -3px 10px 3px var(--top-shadow),
      inset 3px 3px 10px 3px var(--bottom-shadow);
  }

  option {
    background: var(--bg);
    outline: none;
  }
</style>
