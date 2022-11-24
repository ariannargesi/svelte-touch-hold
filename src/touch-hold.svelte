<script>
  export let delay = 2000;
  export let onHold;
  export let tag = "div";
  export let onClick = null;

  let timeoutId;

  if (typeof onHold != "function") throw Error("onHold Must be a function");
  else if (onClick != null && typeof onClick != "function")
    throw Error("onClick must a function");
  else if (typeof delay != "number") throw Error("Delay must be a number");

  const handleTouchStart = () => {
    timeoutId = setTimeout(() => {
      onHold();
    }, delay);
  };

  const handleTouchEnd = () => {
    clearTimeout(timeoutId);
  };
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<svelte:element
  this={tag}
  on:click={onClick}
  on:touchend={handleTouchEnd}
  on:touchstart={handleTouchStart}
>
  <slot />
</svelte:element>
