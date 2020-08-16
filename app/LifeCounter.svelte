<script>
  export let header;

  let life = 20;
  $: alive = (life >= 0);

  function changeLife(n) {
    life += n;
  }
</script>

<stackLayout>
  <label class="header">{header}</label>
  <label class="info" horizontalAlignment="center" verticalAlignment="center" textWrap="true">
    <formattedString class="alive">
      <span text= "{life} " />
      {#if alive}
        <span class="fas alive" text="&#xf004;" />
      {:else}
        <span class="fas dead" text="&#xf54c;" />
      {/if}
    </formattedString>
  </label>
  <flexboxLayout>
    <button on:tap={() => changeLife(-5)}>-5</button>
    <button on:tap={() => changeLife(-1)}>-1</button>
    <button on:tap={() => changeLife(+1)}>+1</button>
    <button on:tap={() => changeLife(+5)}>+5</button>
    <button on:tap={() => life=20} class="reset">RESET</button>
  </flexboxLayout>
</stackLayout>

<style>
  .info .fas {
    color: #FF8888;
    margin: 1em;
  }
  .header {
    text-align: center;
    font-size: 30;
  }
  .info {
    font-size: 20;
  }
  button {
    background-color: blue;
    margin: 0;
  }
  .reset {
    background-color: red;
  }
</style>
