<script>
  let count = 0;
  $: doubled = count * 2;

  function handleClick() {
    count += 1;
  }

  //   $: {
  //     console.log(`the count is ${count}`);
  //     alert(`I SAID THE COUNT IS ${count}`);
  //   }

  //   $: if (count >= 10) {
  //     alert(`count is dangerously high!`);
  //     count = 9;
  //   }

  let numbers = [1, 2, 3, 4];

  function addNumber() {
    numbers = [...numbers, numbers.length + 1];
  }

  $: sum = numbers.reduce((t, n) => t + n, 0);
</script>

<style>
  /* your styles go here */
</style>

<hr />
<button on:click={handleClick}>
  Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>
<hr />
<p>{numbers.join(' + ')} = {sum}</p>

<button on:click={addNumber}>Add a number</button>
