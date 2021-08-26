<script>
  export let showModal = false;
</script>

{#if showModal}
  <div class="backdrop" on:click|self>
    <div class="modal-container">
      <slot />
    </div>
  </div>
{/if}

<style>
  .backdrop {
    position: fixed;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }
  .modal-container {
    width: 300px;
    background-color: currentcolor;
    margin: 14% auto;
    border-radius: 5%;
    padding: 35px;
  }
</style>
