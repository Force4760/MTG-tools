<script>
  import Btn from "../components/Btn.svelte";
  import Slider from "../components/Slider.svelte";
  import PlayerCard from "../components/NewPlayerCard.svelte";
  import Modal from "../components/startModal.svelte";
  let playerNumber = 2;
  let max = 9;
  let min = 1;
  let show = true;
  export let game;
  export let players = [
    ["Player 1", true, true, true, true],
    ["Player 2", true, true, true, true],
  ];
  let lives = [10, 20, 30, 40, 50];
  $: life = Math.floor((bar[0] * (lives.length - 1)) / (bar[1] * 0.8));
  let bar = [120, 450];
  function changeValue(value, delta, min, max, players) {
    let final = value + delta;

    if (final >= min && final <= max) {
      if (delta > 0) {
        players.push([`Player ${players.length + 1}`, true, true, true, true]);
      } else {
        players.pop();
      }

      return [final, players];
    } else if (delta > 0) {
      return [max, players];
    } else {
      return [min, players];
    }
  }
  function createPlayer(player, strtLife) {
    let newPlayer = {
      name: player[0],
      cbless: false,
      monarch: false,
      props: [["images/heart.svg", strtLife]],
    };
    if (player[1]) {
      newPlayer.props.push(["images/P.svg", 0]);
    }
    if (player[2]) {
      newPlayer.props.push(["images/e.svg", 0]);
    }
    if (player[3]) {
      newPlayer.props.push(["images/heart.svg", 0]);
    }
    if (player[4]) {
      newPlayer.props.push(["images/P.svg", 0]);
    }

    return newPlayer;
  }

  function createMultiple(players, strtLife) {
    let playerList = [];
    for (let i = 0; i < players.length; i++) {
      playerList.push(createPlayer(players[i], strtLife));
    }
    return playerList;
  }

  function st(players) {
    game.players = createMultiple(players, lives[life]);
    game.starting = true;
    show = false;
    setTimeout(() => {
      game.pages[0] = true;
      setTimeout(() => {
        game.starting = false;
        setTimeout(() => {
          game.pages[6] = false;
        }, 500);
      }, 1000);
    }, 2000);
  }
</script>

<Modal bind:show={game.starting} />
{#if show}
  <Slider bind:left={bar[0]} bind:size={bar[1]} bind:value={lives[life]} />
  <div class="cards">
    {#each players as play (play)}
      <PlayerCard bind:checks={play} />
    {/each}
  </div>

  <div class="btns">
    <Btn
      width="7rem"
      label="-"
      fun={() => {
        [playerNumber, players] = changeValue(
          playerNumber,
          -1,
          min,
          max,
          players
        );
      }}
    />
    <Btn
      width="7rem"
      fun={() => {
        [playerNumber, players] = changeValue(
          playerNumber,
          1,
          min,
          max,
          players
        );
      }}
    />
  </div>

  <Btn
    font="2rem"
    label="START"
    fun={() => {
      st(players);
    }}
  />
{/if}

<style>
  .cards {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    justify-content: space-evenly;
    width: 100%;
  }
  .btns {
    display: flex;
    width: 90%;
    max-width: 450px;
    margin: auto;
    justify-content: space-between;
  }
</style>
