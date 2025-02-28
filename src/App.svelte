<script>
  import { onMount } from 'svelte';
  let arrayValue = [];
  let selected = "";

  function onPushClick() {
    if (selected === '') return;

    arrayValue = [...arrayValue, arrayValue.length + 1];
  }

  function onPopClick() {
    if (selected === 'stack') {
      arrayValue = arrayValue.slice(0, -1);
    } else if (selected === 'queue') {
      arrayValue = arrayValue.slice(1);
    }
  }
</script>

<style>
  .wrapper-stackqueue { text-align: center; }
  .mode-container, .pushpop-container { display: flex; justify-content: center; gap: 10px; }
  .mode { padding: 10px; border: 1px solid black; cursor: pointer; }
  .stackqueue-container { margin-top: 20px; display: flex; gap: 5px; }
  .stackqueue-value { padding: 10px; border: 1px solid black; }
</style>

<div class="wrapper-stackqueue">
  <div class="wrapper-container">
    <div class="left-container">
      <h2 class='heading-stackqueue'>SELECT MODE</h2>

      <div class="mode-container">
        <button 
          class="mode" 
          style="background-color: {selected === 'stack' ? 'white' : ''}; color: {selected === 'stack' ? 'black' : ''}" 
          on:click={() => selected = 'stack'}>
          STACK
        </button>
        <div class="or">OR</div>
        <button 
          class="mode" 
          style="background-color: {selected === 'queue' ? 'white' : ''}; color: {selected === 'queue' ? 'black' : ''}" 
          on:click={() => selected = 'queue'}>
          QUEUE
      </button>
      </div>

      <h2 class='heading-stackqueue'>SELECT OPERATION</h2>
      <div class="pushpop-container">
        <button class="mode" on:click={onPushClick}>PUSH</button>
        <div class="or">OR</div>
        <button class="mode" on:click={onPopClick}>POP</button>
      </div>
    </div>

    <div class="stackqueue-container">
      {#each arrayValue as val}
        <div class='stackqueue-value'>{val}</div>
      {/each}
    </div>
  </div>
</div>
