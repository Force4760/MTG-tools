<script>
  import Block from "../components/blockcard.svelte";
  import Custom from "../components/customdice.svelte";
</script>

<div class="dices">
  <Block />
  <Block label="D 6" number={6} />
  <Block label="D 8" number={8} />
  <Block label="D 10" number={10} />
  <Block label="D 12" number={12} />
  <Block label="D 20" number={20} />
  <Block label="D 100" number={100} />
  <Custom />
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
