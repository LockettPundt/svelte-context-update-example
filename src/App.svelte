<script>
  import ContextValueExample from './ContextValueExample.svelte';
  import { setContext } from 'svelte';
  import { writable } from 'svelte/store';

  let contextObject = writable({
    value: 'some Initial Value',
    anotherValue: 'some other initial value',
    lastValue: 'the last initial value',
  });

  setContext('value', contextObject);
</script>

<style>
  :global(body) {
    margin: 0;
    font-family: Arial, Helvetica, sans-serif;
  }
</style>

<div class="App">
  <ContextValueExample />
</div>
