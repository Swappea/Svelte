<script>
  // import Reactivity from './Reactivity.svelte';
  // import Props from "./Props.svelte";
  // import Logic from "./Logic.svelte";
  // import Events from "./Events.svelte";
  // import Bindings from "./Bindings.svelte";
  import Lifecycle from "./Lifecycle.svelte";
  export let title = "Svelte Tutorial!";
  //   const propsInfo = {
  // 	  name: 'Props',
  // 	  answer: 42
  //   }

  function handleMessage(event) {
    alert(event.detail.text);
  }

  import { onMount, onDestroy } from "svelte";
  let showLifecycleComp = true;
  onMount(() => {
    setTimeout(() => {
      showLifecycleComp = false;
    }, 10000);
  });
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<h1>{title}</h1>

<!-- <Reactivity/> -->
<!-- <Props {...propsInfo} />
<Props /> -->
<!-- <Logic /> -->
<!-- <Events on:messages={handleMessage} on:message={handleMessage}/> -->
<!-- <Bindings /> -->
{#if showLifecycleComp}
  <Lifecycle />
{/if}
