<script>
  // import Reactivity from './Reactivity.svelte';
  // import Props from "./Props.svelte";
  // import Logic from "./Logic.svelte";
  import Events from "./Events.svelte";
  export let title = "Svelte Tutorial!";
  //   const propsInfo = {
  // 	  name: 'Props',
  // 	  answer: 42
  //   }

  function handleMessage(event) {
    alert(event.detail.text);
  }
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
<Events on:messages={handleMessage} on:message={handleMessage}/>
