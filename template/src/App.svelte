<script>
  // import Reactivity from './Reactivity.svelte';
  // import Props from "./Props.svelte";
  // import Logic from "./Logic.svelte";
  // import Events from "./Events.svelte";
  // import Bindings from "./Bindings.svelte";
  // import Lifecycle from "./Lifecycle.svelte";
  import Tweened from "./Tweened.svelte";
  import Spring from "./Spring.svelte";

  export let title = "Svelte Tutorial!";

  // import { count, name, greeting } from "./stores.js";
  // import Incrementer from "./Incrementer.svelte";
  // import Decrementer from "./Decrementer.svelte";
  // import Timer from "./Timer.svelte";
  //   const propsInfo = {
  // 	  name: 'Props',
  // 	  answer: 42
  //   }

  // function handleMessage(event) {
  //   alert(event.detail.text);
  // }

  // import { onMount, onDestroy } from "svelte";
  // let showLifecycleComp = true;
  // onMount(() => {
  //   setTimeout(() => {
  //     showLifecycleComp = false;
  //   }, 10000);
  // });

  // let count_value;

  // const unsubscribe = count.subscribe(value => {
  //   count_value = value;
  // });
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
<!-- {#if showLifecycleComp}
  <Lifecycle />
{/if} -->

<!-- <h1>The count is {count_value}</h1> -->
<!-- Shortcut for unsubscription or else do this onDestroy(unsubscribe); -->
<!-- $variable is reserved for store reference value -->
<!-- <h1>The count is {$count}</h1>

<Incrementer />
<Decrementer /> -->
<!-- <Timer />

<h1>The count is {$count}</h1>

<button on:click={count.increment}>+</button>
<button on:click={count.decrement}>-</button>
<button on:click={count.reset}>reset</button>

<h1>{$greeting}</h1>
<input bind:value={$name}>

<button on:click="{() => $name += '!'}">
	Add exclamation mark!
</button> -->

<Tweened />
<Spring />
