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
  {#if alive}
    <label class="info" horizontalAlignment="center" verticalAlignment="center" textWrap="true">
      <formattedString>
        <span text= "{life} " />
        <span class="fas alive" text="&#xf004;" />
      </formattedString>
    </label>
  {:else}
    <label class="info" horizontalAlignment="center" verticalAlignment="center" textWrap="true">
      <formattedString>
        <span text= "{life} " />
        <span class="fas dead" text="&#xf54c;" />
      </formattedString>
    </label>
  {/if}
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
    margin: 1em;
  }
  .dead {
    color: #770077;
  }
  .alive {
    color: #FF8888;
  }
  .header {
    text-align: center;
    font-size: 30;
  }
  .info {
    font-size: 20;
  }
  button {
    background-color: #1188CC;
    margin: 0;
  }
  .reset {
    background-color: red;
  }
</style>
