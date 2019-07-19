<script>
  let user = {
    loggedIn: false
  };

  function toggle() {
    user.loggedIn = !user.loggedIn;
  }

  let number = 7;

  let cats = [
    { id: "J---aiyznGQ", name: "Keyboard Cat" },
    { id: "z_AbfPXTKms", name: "Maru" },
    { id: "OUtn3pvWmpg", name: "Henri The Existential Cat" }
  ];

  function handleClick() {
    cats = cats.slice(1);
  }

  let promise = getRandomNumber(Math.floor(Math.random() * 10) + 1  );

  async function getRandomNumber(index) {
    const res = await fetch(`https://jsonplaceholder.typicode.com/todos/${index}`);
    const text = await res.text();

    if (res.ok) {
      return text;
    } else {
      throw new Error(text);
    }
  }

  function handleRandomNumberClick() {
    let index = Math.floor(Math.random() * 10) + 1;
    promise = getRandomNumber(index);
  }
</script>

<style>

</style>

<hr />
<h4>if blocks</h4>
<!-- {#if user.loggedIn}
  <button on:click={toggle}>Log out</button>
{/if}

{#if !user.loggedIn}
  <button on:click={toggle}>Log in</button>
{/if} -->

<hr />
<h4>if else blocks</h4>
{#if user.loggedIn}
  <button on:click={toggle}>Log out</button>
{:else}
  <button on:click={toggle}>Log in</button>
{/if}

<hr />
<h4>if elseif blocks</h4>
{#if number > 10}
  <p>{number} is greater than 10</p>
{:else if 5 > number}
  <p>{number} is less than 5</p>
{:else}
  <p>{number} is between 5 and 10</p>
{/if}

<hr />
<h4>Each blocks</h4>
<ul>
  {#each cats as { id, name }, i (id)}
    <li>
      <a target="_blank" href="https://www.youtube.com/watch?v={id}">
        {i + 1}: {name}
      </a>
    </li>
  {/each}
</ul>

<button on:click={handleClick}>Remove first cat</button>

<hr />
<h4>Await blocks</h4>
<button on:click={handleRandomNumberClick}>generate random number</button>

{#await promise}
	<p>...waiting</p>
{:then jsonData}
	<p>The json is {jsonData}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
