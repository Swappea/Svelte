<script>
  // import MediaBindings from './MediaBindings.svelte';
  // import Canvasbinding from './Canvasbinding.svelte';

  let name = "world";
  let a = 1;
  let b = 2;
  let yes = false;

  let scoops = 1;
  let flavours = ["Mint choc chip"];
  let menu = ["Cookies and cream", "Mint choc chip", "Raspberry ripple"];

  function join(flavours) {
    if (flavours.length === 1) return flavours[0];
    return `${flavours.slice(0, -1).join(", ")} and ${
      flavours[flavours.length - 1]
    }`;
  }

  let textAreaValue = `This is a textarea statement`;

  let questions = [
    { id: 1, text: `Where did you go to school?` },
    { id: 2, text: `What is your mother's name?` },
    {
      id: 3,
      text: `What is another personal fact that an attacker could easily find with Google?`
    }
  ];

  let selected = 1;
  let cities = ["Mumbai", "Bangalore", "Delhi"];
  let selectedCities = ["Mumbai"];
  let contentHtml = "<p>Write some text!</p>";

  let todos = [
    { done: false, text: "finish Svelte tutorial" },
    { done: false, text: "build an app" },
    { done: false, text: "world domination" }
  ];

  $: todoRemaining = todos.filter(t => !t.done).length;
</script>

<style>
  textarea {
    width: 50%;
    height: 200px;
  }

  [contenteditable] {
    padding: 0.5em;
    border: 1px solid #eee;
    border-radius: 4px;
  }
</style>

<hr />
<h4>Bindings Tutorial</h4>
<input bind:value={name} />
<h1>Hello {name}!</h1>

<hr />
<h4>Numbers Binding</h4>
<label>
  <input type="number" bind:value={a} min="0" max="10" />
  <input type="range" bind:value={a} min="0" max="10" />
</label>

<label>
  <input type="number" bind:value={b} min="0" max="10" />
  <input type="range" bind:value={b} min="0" max="10" />
</label>

<p>{a} + {b} = {a + b}</p>

<hr />
<h4>Checkbox binding</h4>
<input type="checkbox" bind:checked={yes} />
{#if yes}
  <p>Yay its checked!!!!!</p>
{:else}
  <p>Unchecked :(</p>
{/if}

<hr />
<h4>Group Inputs Binding</h4>
<h2>Size</h2>

<label>
  <input type="radio" bind:group={scoops} value={1} />
  One scoop
</label>

<label>
  <input type="radio" bind:group={scoops} value={2} />
  Two scoops
</label>

<label>
  <input type="radio" bind:group={scoops} value={3} />
  Three scoops
</label>

<h2>Flavours</h2>

{#each menu as flavour}
  <label>
    <input type="checkbox" bind:group={flavours} value={flavour} />
    {flavour}
  </label>
{/each}

{#if flavours.length === 0}
  <p>Please select at least one flavour</p>
{:else if flavours.length > scoops}
  <p>Can't order more flavours than scoops!</p>
{:else}
  <p>
    You ordered {scoops} {scoops === 1 ? 'scoop' : 'scoops'} of {join(flavours)}
  </p>
{/if}

<hr />
<h4>Textarea binding</h4>
<textarea bind:value={textAreaValue} />
<p>{textAreaValue}</p>

<hr />
<h4>Select Binding</h4>
<select bind:value={selected}>
  {#each questions as question}
    <option value={question.id}>{question.text}</option>
  {/each}
</select>
<p>Selected id: {selected}</p>

<hr />
<h4>Multiple Select binding</h4>
<select multiple bind:value={selectedCities}>
  {#each cities as city}
    <option value={city}>{city}</option>
  {/each}
</select>
{#each selectedCities as selectedCity}
  <p>{selectedCity}</p>
{/each}

<hr />
<h4>Content Editable Bindings</h4>
<div contenteditable="true" bind:innerHTML={contentHtml} />
<pre>{contentHtml}</pre>

<hr />
<h4>Each Block binding(Direct mutation)</h4>
{#each todos as todo}
  <input type="checkbox" bind:checked={todo.done} />
  <input type="text" bind:value={todo.text} />
  <p></p>
{/each}
<p>todo's remainining: {todoRemaining}</p>

<!-- <hr>
<h4>Media Bindings</h4>
<MediaBindings /> -->

<!-- <hr>
<h4>Canvas Bindings</h4>
<Canvasbinding /> -->