<script>
  import Card from "../components/Card.svelte";
  export let game;
</script>

<div class="cards">
  {#each game.players as player (player)}
    <Card bind:values={player} />
  {/each}
</div>

<style>
  .cards {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-evenly;
    width: 100%;
  }
</style>
