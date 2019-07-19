<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function sayHello() {
    dispatch("message", {
      text: "Hello from child of child of app!"
    });
  }
</script>

<style>

</style>

<button on:click={sayHello}>Click to say hello</button>
<button on:click>Click to forward click event</button>