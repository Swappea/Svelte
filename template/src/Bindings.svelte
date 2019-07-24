<script>
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
</script>

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
