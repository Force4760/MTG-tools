<script>
  import { slide } from "svelte/transition";
  export let values = {
    props: [["images/heart.svg", 10][("images/heart.svg", 20)]],
  };
  let index = 0;

  function changeValue(value, delta) {
    let final = value + delta;
    return final;
  }
  function changeValueMin(value, delta, min) {
    let final = value + delta;
    if (final >= min) {
      return final;
    } else {
      return min;
    }
  }
  function changeValueWrap(value, delta, max, min) {
    let final = value + delta;
    if (final < min) {
      return max;
    } else if (final > max) {
      return min;
    } else {
      return final;
    }
  }

  function keys(e) {
    switch (e.keyCode) {
      case 37:
        index = changeValueWrap(index, -1, values.props.length - 1, 0);
        break;
      case 38:
        values.props[index][1] = changeValue(values.props[index][1], 1);
        break;
      case 39:
        index = changeValueWrap(index, 1, values.props.length - 1, 0);
        break;
      case 40:
        values.props[index][1] = changeValueMin(values.props[index][1], -1, 0);
        break;
    }
  }
</script>

<div
  class="card"
  tabindex="0"
  on:keydown={keys}
  transition:slide={{ duration: 300 }}
>
  <p class="name">{values.name}</p>
  <img src={values.props[index][0]} alt="of the value" />
  <div class="value">{values.props[index][1]}</div>
  <div
    class="add change"
    on:click={() =>
      (values.props[index][1] = changeValue(values.props[index][1], 1))}
  />
  <div
    class="minus change"
    on:click={() =>
      (values.props[index][1] = changeValueMin(values.props[index][1], -1, 0))}
  />
  {#if values.props.length > 1}
    <div
      class="prev change"
      on:click={() =>
        (index = changeValueWrap(index, -1, values.props.length - 1, 0))}
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        ><path
          fill="rgb(200, 200, 200)"
          d="M5 3l3.057-3 11.943 12-11.943 12-3.057-3 9-9z"
        /></svg
      >
    </div>
    <div
      class="next change"
      on:click={() =>
        (index = changeValueWrap(index, 1, values.props.length - 1, 0))}
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        ><path
          fill="rgb(200, 200, 200)"
          d="M5 3l3.057-3 11.943 12-11.943 12-3.057-3 9-9z"
        /></svg
      >
    </div>
  {/if}
</div>

<style>
  p.name {
    position: absolute;
    top: 5%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 100%;
    z-index: -1;
    text-align: center;
    font-size: 1.5rem;
  }
  img {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 55%;
    opacity: 0.1;
    z-index: -2;
  }
  .value {
    z-index: -1;
    font-size: 5rem;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  .add {
    border-top-left-radius: 25px;
    border-top-right-radius: 25px;
    width: 100%;
    height: 50%;
  }
  .minus {
    border-bottom-left-radius: 25px;
    border-bottom-right-radius: 25px;
    width: 100%;
    height: 50%;
  }

  .card {
    position: relative;
    height: 270px;
    margin-left: 2rem;
    margin-right: 2rem;
    margin-top: 2rem;
    width: 90%;
    max-width: 450px;
    border-radius: 25px;
    background: rgba(10, 10, 10, 0.05);
    box-shadow: -3px -3px 10px 5px var(--top-shadow),
      3px 3px 10px 5px var(--bottom-shadow);
    transform: 2s;
  }
  .prev {
    position: absolute;
    border-bottom-left-radius: 25px;
    border-top-left-radius: 25px;
    width: 15%;
    height: 100%;
    top: 0%;
    left: 0%;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .prev svg {
    transform: scaleX(-1);
  }

  .next {
    position: absolute;
    border-bottom-right-radius: 25px;
    border-top-right-radius: 25px;
    top: 0%;
    right: 0%;
    width: 15%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .change {
    transition: ease-in 0.2s;

    color: var(--text-main);
  }
  .change:hover {
    background-color: rgba(10, 10, 10, 0.1);
  }

  @media (max-width: 600px) {
    .next,
    .prev {
      width: 20%;
    }
  }
</style>
