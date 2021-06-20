<script>
  import TextBox from "../components/TextBox.svelte";
  import Select from "../components/Select.svelte";
  import Toggle2 from "../components/Toggle2.svelte";
  import Btn from "../components/Btn.svelte";
  let name = "";
  let typeLine = "";
  let text = "";
  let cost = "";
  let colors = [false, false, false, false, false, false];
  let rarity = [false, false, false, false];
  let order = "name";
  function colorFun(colors) {
    let colorStr = "";
    if (colors[0]) {
      colorStr += "W";
    }
    if (colors[1]) {
      colorStr += "U";
    }
    if (colors[2]) {
      colorStr += "B";
    }
    if (colors[3]) {
      colorStr += "R";
    }
    if (colors[4]) {
      colorStr += "G";
    }
    if (colors[5]) {
      colorStr += "C";
    }
    return colorStr;
  }
  function rareFun(rarity) {
    let rareStr = "";
    if (rarity[0]) {
      rareStr += "c";
    }
    if (rarity[1]) {
      rareStr += "u";
    }
    if (rarity[2]) {
      rareStr += "r";
    }
    if (rarity[3]) {
      rareStr += "m";
    }

    return rareStr;
  }
  function openUrl(name, type, text, cost, colors, rarity, order) {
    name = encodeURIComponent(name);
    text = encodeURIComponent(text);
    type = encodeURIComponent(type);
    cost = encodeURIComponent(cost);
    let color = colorFun(colors);
    let rare = rareFun(rarity);
    let url = "https://scryfall.com/search?as=grid&order=" + order + "&q=";
    if (name) {
      url += name;
    }
    if (text) {
      url += "+oracle%3A" + text;
    }
    if (type) {
      url += "+type%3A" + type;
    }
    if (cost) {
      url += "+mana%3A" + cost;
    }
    if (color) {
      url += "+commander%3A" + color;
    }
    if (rare) {
      url += "+rarity%3A" + rare;
    }
    window.open(url);
  }
</script>

<div class="container">
  <div class="text-boxes">
    <TextBox max="" margin="2rem" bind:value={name} />
    <TextBox
      placeholder="Type Line"
      max=""
      margin="2rem"
      bind:value={typeLine}
    />
    <TextBox placeholder="Text" max="" margin="2rem" bind:value={text} />
    <TextBox placeholder="Mana Cost" max="" margin="2rem" bind:value={cost} />
    <Select margin="2rem" bind:value={order} />
  </div>

  <div class="colors">
    <Toggle2 bind:value={colors[0]} label="W" />
    <Toggle2 bind:value={colors[1]} label="U" />
    <Toggle2 bind:value={colors[2]} label="B" />
    <Toggle2 bind:value={colors[3]} label="R" />
    <Toggle2 bind:value={colors[4]} label="G" />
    <Toggle2 bind:value={colors[5]} label="C" />
  </div>
  <div class="rarity">
    <Toggle2 bind:value={rarity[0]} label="Common" />
    <Toggle2 bind:value={rarity[1]} label="Uncommon" />
    <Toggle2 bind:value={rarity[2]} label="Rare" />
    <Toggle2 bind:value={rarity[3]} label="Mythic Rare" />
  </div>
  <Btn
    label="Search"
    font="2rem"
    fun={() => openUrl(name, typeLine, text, cost, colors, rarity, order)}
  />
</div>

<style>
  .container {
    margin: auto;
    width: 90%;
    max-width: 900px;
  }
  .rarity,
  .colors {
    margin: 2rem auto;
    padding: 1rem;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    max-width: 90%;
  }
</style>
