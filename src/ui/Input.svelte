<script>

  let className;
  export { className as class };

  export let value;
  export let placeholder;

</script>

<input
  type="text"
  class={`bg-near-white bn pa3 ${className || ''}`}
  placeholder={placeholder}
  bind:value={value}
>
