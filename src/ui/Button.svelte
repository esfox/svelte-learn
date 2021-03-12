<script>

  export let onClick;

  let className;
  export { className as class };

</script>

<button
  class={`bg-green white fw7 bn br-pill shadow-hover pa3 pointer ${className || ''}`}
  on:click={onClick}
>
  <slot />
</button>
