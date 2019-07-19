<script>
  import { createEventDispatcher } from "svelte";
  import EventsChild from "./EventsChild.svelte";
  const dispatch = createEventDispatcher();

  function sayHello() {
    dispatch("messages", {
      text: "Hello from child of app!"
    });
  }

  let mq = { x: 0, y: 0 };
  let m = { x: 0, y: 0 };

  function handleMousemove(event) {
    mq.x = event.clientX;
    mq.y = event.clientY;
  }

  function handleClick() {
    alert("no more alerts");
  }

  function handleEventsChildClick() {
      alert("Click event from events child is forwarded to Events");
  }
</script>

<style>
  div {
    width: 40%;
    height: 40%;
    border: 1px solid black;
  }
</style>

<hr />
<h4>Events Tutorial</h4>
<div on:mousemove={handleMousemove}>The mouse position is {mq.x} x {mq.y}</div>

<hr />
<h4>Inline Events handler</h4>
<div on:mousemove={e => (m = { x: e.clientX, y: e.clientY })}>
  The mouse position is {m.x} x {m.y}
</div>

<hr />
<h4>Event Modifiers</h4>
<button on:click|once={handleClick}>Click me</button>

<hr />
<h4>Event Dispatcher</h4>
<button on:click={sayHello}>Click to say hello</button>

<hr />
<h4>Event Forwarding</h4>
<EventsChild on:message on:click={handleEventsChildClick}/>
