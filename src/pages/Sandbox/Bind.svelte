<script>
  import Button from '../../ui/Button.svelte';
  import Input from '../../ui/Input.svelte';

  let name = '';
  let job = '';
  let person =
  {
    name: 'John',
    job: 'Developer',
  };

  const updatePerson = () => person = { name, job };

  let property = '';
  let value = '';

  /** @type {HTMLElement}*/
  let error;
  const updateProperty = () => {
    const setErrorText = text => error.textContent = text;

    if (! person[property])
      return setErrorText("Whoops, that's not a valid property!");

    setErrorText();
    person[property] = value;
  };
</script>

<div class="mt4">
  <Input class="mr2" placeholder="Enter a name" bind:value={name} />
  <Input placeholder="Enter a job" bind:value={job} />
  <Button class="ml3" onClick={updatePerson}>Try click 🧐</Button>
  <div class="mt3">
    <div>
      The name you typed: <h4 class="di">{name}</h4>
    </div>
    <div class="mt2">
      The job you typed: <h4 class="di">{job}</h4>
    </div>
  </div>
  <code class="db bg-near-white black pa3 mt3 mb4">
    {JSON.stringify(person)}
  </code>
  <div>
    <Input
      class="mr2"
      placeholder="What property to update?"
      bind:value={property}
    />
    <Input placeholder="Value of the property?" bind:value />
    <Button class="ml3" onClick={updateProperty}>Try click again 🧐</Button>
    <div class="light-red mt2" bind:this={error} />
  </div>
</div>
