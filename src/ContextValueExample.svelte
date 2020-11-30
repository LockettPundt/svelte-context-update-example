<script>
  import { getContext } from 'svelte';
  // using $myContext works the same as subdcribing
  let myContext = getContext('value');
  // let myContextValue;
  let inputValue = '';
  // subscribing to the context on mount
  // onMount(() => myContext.subscribe((value) => (myContextValue = value)));

  const updateContext = (valueName) => {
    return myContext.update((store) => {
      store[valueName] = inputValue;
      return store;
    });
  };
  const activeToggle = () => {
    return myContext.update((store) => {
      store.active = !store.active;
      return store;
    });
  };
</script>

<style>
  h1.active {
    color: green;
  }
</style>

<h1 class:active={$myContext.active}>1. {$myContext?.value}</h1>
<h1>2. {$myContext?.anotherValue}</h1>
<h1>3. {$myContext?.lastValue}</h1>
<input bind:value={inputValue} placeholder="edit context values" />
<label name="active">
  click to toggle active state.
  <input type="checkbox" htmlfor="active" on:click={activeToggle} />
</label>
<button on:click={() => updateContext('value')}>update value One</button>
<button on:click={() => updateContext('anotherValue')}>update value Two</button>
<button on:click={() => updateContext('lastValue')}>update value Three</button>
<button on:click={() => console.log($myContext)}>console log the value</button>
