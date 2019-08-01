<script>
  import { onMount, onDestroy, beforeUpdate, afterUpdate, tick } from "svelte";
  let photos = [];
  console.log("Script Tag");
  beforeUpdate(() => {
    console.log("Before Update");
  });

  onMount(async () => {
    console.log("On Mount");
    const res = await fetch(
      `https://jsonplaceholder.typicode.com/photos?_limit=20`
    );
    photos = await res.json();
  });

  afterUpdate(() => {
    console.log("After Update");
  });

  onDestroy(() => {
    console.log("On Destroy");
    photos = [];
  });

  let text = `Select some text and hit the tab key to toggle uppercase`;

  async function handleKeydown(event) {
    if (event.which !== 9) return;

    event.preventDefault();

    const { selectionStart, selectionEnd, value } = this;
    const selection = value.slice(selectionStart, selectionEnd);

    const replacement = /[a-z]/.test(selection)
      ? selection.toUpperCase()
      : selection.toLowerCase();

    text =
      value.slice(0, selectionStart) + replacement + value.slice(selectionEnd);

    await tick();
    this.selectionStart = selectionStart;
    this.selectionEnd = selectionEnd;
  }
</script>

<style>
  .photos {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    grid-gap: 8px;
  }

  figure,
  img {
    width: 100%;
    margin: 0;
  }

  textarea {
    width: 100%;
    height: 200px;
  }
</style>

<h1>Photo album</h1>

<div class="photos">
  {#each photos as photo}
    <figure>
      <img src={photo.thumbnailUrl} alt={photo.title} />
      <figcaption>{photo.title}</figcaption>
    </figure>
  {:else}
    <!-- this block renders when photos.length === 0 -->
    <p>loading...</p>
  {/each}
</div>

<hr />
<h4>Tick</h4>
<textarea value={text} on:keydown={handleKeydown} />
