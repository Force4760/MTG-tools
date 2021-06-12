<script>
  import Dice from "./pages/dices.svelte";
  import Nav from "./pages/nav.svelte";
  import StartG from "./pages/StartGame.svelte";
  import CS from "./components/comingsoon.svelte";
  import Mana from "./pages/manaPage.svelte";
  import Playing from "./pages/Playing.svelte";
  import Footer from "./components/Footer.svelte";
  let game = {
    pages: [false, false, false, false, false, false, true],
    mana: {
      W: 0,
      U: 0,
      B: 0,
      R: 0,
      G: 0,
      C: 0,
      S: 0,
    },
    players: [
      {
        name: "Player 1",
        cbless: false,
        monarch: false,
        props: [["images/heart.svg", 20]],
      },
    ],
    starting: false,
  };
</script>

<div class="game">
  <Nav bind:game />
  {#if game.pages[0]}
    <Playing bind:game />
  {:else if game.pages[1]}
    <Dice />
  {:else if game.pages[2]}
    <Mana bind:game />
  {:else if game.pages[3]}
    <CS />
  {:else if game.pages[4]}
    <CS />
  {:else if game.pages[5]}
    <CS />
  {:else if game.pages[6]}
    <StartG bind:game />
  {/if}
</div>

<style>
  .game {
    min-height: 100%;
    padding-bottom: 3rem;
  }
</style>
