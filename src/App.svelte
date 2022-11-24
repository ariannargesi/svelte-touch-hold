<script>
  import TouchHold from "./touch-hold.svelte";

  let showMessage = false;
  const saySomething = () => {
    showMessage = true;
  };
</script>

<TouchHold
  tag={"button"}
  onHold={saySomething}
  onClick={() => {
    console.log("Hello world");
  }}
  delay={2000}
>
  Press me for two seconds!
</TouchHold>

<div style="margin-top: 40px ;">
  <span> Been held for two seconds? </span>
  {#if showMessage}
    ✅
  {:else}
    ❌
  {/if}
</div>

<style>
  :global(button:hover) {
    background-color: darkgray;
  }
</style>
