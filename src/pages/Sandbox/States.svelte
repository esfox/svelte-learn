<script>
  import Button from '../../ui/Button.svelte';

  let count = 0;
  const increment = () => count++;
  $: doubled = count * 2;
  $: {
    console.log('This block is called whenever `count` and `doubled` changes.');
    console.log(count);
    console.log(doubled);
  }

  let list = [1, 2, 3, 4, 5];
</script>

<div class="flex items-center">
  <Button onClick={increment}>Click!</Button>
  <h1 class="ml4">{count}</h1>
  <h2 class="ml4">Doubled is {doubled}</h2>
</div>

<div class="mt4">
  <Button onClick={() => list = [...list, list.length + 1]}>
    Click to add to the array
  </Button>
  <pre class="mt4">
    {JSON.stringify(list)}
  </pre>
</div>
