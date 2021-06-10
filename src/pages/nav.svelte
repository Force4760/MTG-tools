<script>
  import { slide, fade } from "svelte/transition";
  import Btn from "../components/Btn.svelte";
  export let game;
  let show = false;
  function showModal() {
    show = !show;
  }
  function changePage(n) {
    showModal();
    for (let i = 0; i < game.pages.length; i++) {
      game.pages[i] = false;
    }
    setTimeout(function () {
      game.pages[n] = true;
    }, 350);
  }
  function reset() {
    game = {
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
    setTimeout(function () {
      showModal();
    }, 100);
  }
</script>

<nav>
  <h1>MTG TOOLS</h1>
  <Btn
    width="8rem"
    label="Menu"
    font=""
    marginTop="none"
    margin="none"
    fun={showModal}
  />
</nav>
{#if show}
  <div class="out" transition:fade={{ duration: 800 }} on:click={showModal} />
  <div class="modal" transition:slide={{ delay: 200, duration: 700 }}>
    <Btn
      width="90%"
      label="Back to Game"
      font="1.5rem"
      marginTop="none"
      margin="auto"
      fun={() => changePage(0)}
    />
    <Btn
      width="90%"
      label="Dice"
      font="1.5rem"
      marginTop="none"
      margin="auto"
      fun={() => changePage(1)}
    />
    <Btn
      width="90%"
      label="Mana"
      font="1.5rem"
      marginTop="none"
      margin="auto"
      fun={() => changePage(2)}
    />
    <Btn
      width="90%"
      label="Archenemy"
      font="1.5rem"
      marginTop="none"
      margin="auto"
      fun={() => changePage(3)}
    />
    <Btn
      width="90%"
      label="Planechase"
      font="1.5rem"
      marginTop="none"
      margin="auto"
      fun={() => changePage(4)}
    />
    <Btn
      width="90%"
      label="Search"
      font="1.5rem"
      marginTop="none"
      margin="auto"
      fun={() => changePage(5)}
    />
    <Btn
      width="90%"
      label="New Game"
      font="1.5rem"
      marginTop="none"
      margin="auto"
      fun={reset}
    />
  </div>
{/if}

<style>
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 2rem;
    margin: auto;
    height: 4rem;
    width: 90%;
  }
  @media (min-width: 1000px) {
    nav {
      max-width: 450px;
    }
  }
  .out {
    z-index: 99;
    width: 100%;
    height: 100%;
    background: rgb(15, 105, 165);
    position: absolute;
    top: 0;
    left: 0;
  }
  .modal {
    display: flex;
    flex-direction: column;
    z-index: 100;
    background: rgba(10, 10, 10, 0.05);
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 85vw;
    height: 85vh;
    max-width: 40rem;
    border-radius: 25px;
    box-shadow: -3px -3px 6px 3px var(--top-shadow),
      3px 3px 6px 3px var(--bottom-shadow);
  }
</style>
