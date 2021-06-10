<div>
  <h2>Work in progress</h2>
  <svg
    class="shadow"
    version="1.1"
    id="L5"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    x="0px"
    y="0px"
    viewBox="0 0 60 100"
    enable-background="new 0 0 0 0"
    xml:space="preserve"
  >
    <circle
      class="h"
      fill="rgb(15, 105, 165)"
      stroke="none"
      cx="6"
      cy="50"
      r="6"
    >
      <animateTransform
        attributeName="transform"
        dur="1s"
        type="translate"
        values="0 15 ; 0 -15; 0 15"
        repeatCount="indefinite"
        begin="0.1"
      />
    </circle>
    <circle
      class="h"
      fill="rgb(15, 105, 165)"
      stroke="none"
      cx="30"
      cy="50"
      r="6"
    >
      <animateTransform
        attributeName="transform"
        dur="1s"
        type="translate"
        values="0 10 ; 0 -10; 0 10"
        repeatCount="indefinite"
        begin="0.2"
      />
    </circle>
    <circle
      class="h"
      fill="rgb(15, 105, 165)"
      stroke="none"
      cx="54"
      cy="50"
      r="6"
    >
      <animateTransform
        attributeName="transform"
        dur="1s"
        type="translate"
        values="0 5 ; 0 -5; 0 5"
        repeatCount="indefinite"
        begin="0.3"
      />
    </circle></svg
  >
</div>

<style>
  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    width: 100%;
    height: 35rem;
    padding-top: 5rem;
  }
  h2 {
    text-align: center;
    font-size: 3rem;
    margin-bottom: 2rem;
  }
  svg {
    width: 20%;
    margin: auto;
  }
  .shadow {
    -webkit-filter: drop-shadow(-3px -3px 6px var(--top-shadow))
      drop-shadow(3px 3px 6px var(--bottom-shadow));
    filter: drop-shadow(-3px -3px 6px var(--top-shadow))
      drop-shadow(3px 3px 6px var(--bottom-shadow));
  }
</style>
