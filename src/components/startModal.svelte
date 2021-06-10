<script>
  import { fade } from "svelte/transition";
  export let show = true;
</script>

{#if show}
  <div class="out" transition:fade={{ duration: 300 }} />
  <h3>Fight</h3>
  <svg width="200" height="200" viewBox="0 0 100 100">
    <polyline
      class="line-cornered stroke-still shadow"
      points="0,0 100,0 100,100"
      stroke-width="10"
      fill="none"
    />
    <polyline
      class="line-cornered stroke-still shadow"
      points="0,0 0,100 100,100"
      stroke-width="10"
      fill="none"
    />
    <polyline
      class="line-cornered stroke-animation "
      points="0,0 100,0 100,100"
      stroke-width="10"
      fill="none"
    />
    <polyline
      class="line-cornered stroke-animation "
      points="0,0 0,100 100,100"
      stroke-width="10"
      fill="none"
    />
  </svg>
{/if}

<style>
  .out {
    z-index: 99;
    width: 100%;
    height: 100%;
    background: rgb(15, 105, 165);
    position: absolute;
    top: 0;
    left: 0;
  }
  h3 {
    z-index: 100;
    position: absolute;
    top: 46%;
    left: 50%;
    font-size: 2.2rem;
    -webkit-transform: translate(-50%, -50%) rotate(45deg) scale(1);
    transform: translate(-50%, -50%);
  }
  svg {
    z-index: 100;
    position: absolute;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-50%, -50%) rotate(45deg) scale(1);
    transform: translate(-50%, -50%) rotate(45deg) scale(1);
  }

  .stroke-still {
    stroke: rgb(15, 105, 165);
  }
  .shadow {
    -webkit-filter: drop-shadow(-3px -3px 6px var(--top-shadow))
      drop-shadow(3px 3px 6px var(--bottom-shadow));
    filter: drop-shadow(-5px -5px 6px var(--top-shadow))
      drop-shadow(5px 5px 6px var(--bottom-shadow));
  }

  .stroke-animation {
    -webkit-animation: stroke-spacing 1.2s ease-in, stroke-color 4.8s linear;
    animation: stroke-spacing 1.2s ease-in, stroke-color 4.8s linear;
    -webkit-animation-iteration-count: infinite;
    animation-iteration-count: infinite;
    -webkit-animation-delay: 0;
    animation-delay: 0;
    -webkit-animation-direction: normal;
    animation-direction: normal;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
    -webkit-animation-play-state: running;
    animation-play-state: running;
    -webkit-transform-origin: center center;
    transform-origin: center center;
  }

  @-webkit-keyframes stroke-spacing {
    0% {
      stroke-dasharray: 0 200;
    }
    45% {
      stroke-dashoffset: 0;
      stroke-dasharray: 200 200;
    }
    90% {
      stroke-dashoffset: -200;
      stroke-dasharray: 200 200;
    }
    100% {
      stroke-dashoffset: -200;
      stroke-dasharray: 200 200;
    }
  }

  @keyframes stroke-spacing {
    0% {
      stroke-dasharray: 0 200;
    }
    45% {
      stroke-dashoffset: 0;
      stroke-dasharray: 200 200;
    }
    90% {
      stroke-dashoffset: -200;
      stroke-dasharray: 200 200;
    }
    100% {
      stroke-dashoffset: -200;
      stroke-dasharray: 200 200;
    }
  }

  @-webkit-keyframes stroke-color {
    0% {
      stroke: rgb(0, 100, 200);
    }

    25% {
      stroke: rgb(200, 200, 200);
    }
    50% {
      stroke: rgb(0, 100, 200);
    }
    75% {
      stroke: rgb(200, 200, 200);
    }
    100% {
      stroke: rgb(0, 100, 200);
    }
  }

  @keyframes stroke-color {
    0% {
      stroke: rgb(0, 100, 200);
    }

    25% {
      stroke: rgb(200, 200, 200);
    }
    50% {
      stroke: rgb(0, 100, 200);
    }
    75% {
      stroke: rgb(200, 200, 200);
    }
    100% {
      stroke: rgb(0, 100, 200);
    }
  }
</style>
