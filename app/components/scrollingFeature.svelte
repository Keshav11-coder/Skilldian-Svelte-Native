<script>
  import { onMount, onCleanup } from 'svelte';
  import { spring } from 'svelte/motion';
  import { fade } from 'svelte/transition';

  let isPopupVisible = false;
  let items = [1]; // Single item for the each block

  onMount(() => {
    // Show the popup
    isPopupVisible = true;
  });

  onCleanup(() => {
    // Hide the popup
    isPopupVisible = false;
  });
</script>

<style>
  .popup-container {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    top: 0;
    display: flex;
    justify-content: center;
    align-items: flex-end;
  }

  .popup {
    width: 100%;
    max-height: 80%;
    background-color: #fff;
    padding: 16px;
    border-radius: 8px 8px 0 0;
  }
</style>

<button on:click={() => (isPopupVisible = true)}>Open Popup</button>

{#each items as item (item)}
  {#if isPopupVisible}
    <div class="popup-container" transition:fade>
      <div class="popup">
        <!-- Popup content goes here -->
        <p>This is the popup content.</p>
        <button on:click={() => (isPopupVisible = false)}>Close</button>
      </div>
    </div>
  {/if}
{/each}
