<script>
  import Mana from "../components/mana.svelte";
  export let game;
</script>

<div class="dices">
  <Mana manasymbol="W" bind:result={game.mana.W} />
  <Mana manasymbol="U" bind:result={game.mana.U} />
  <Mana manasymbol="B" bind:result={game.mana.B} />
  <Mana manasymbol="R" bind:result={game.mana.R} />
  <Mana manasymbol="G" bind:result={game.mana.G} />
  <Mana manasymbol="C" bind:result={game.mana.C} />
  <Mana width="50rem" mwidth="85%" bind:result={game.mana.S} />
</div>

<style>
  .dices {
    display: flex;
    flex-wrap: wrap;
    width: 90%;
    max-width: 450px;
    margin: auto;
    align-items: center;
    justify-content: space-between;
  }
</style>
