<script lang="ts">
  import chatIconUrl from '../assets/chat2.png';
  let open = false;
</script>

<!-- svelte-ignore options_missing_custom_element -->
<style>
  :host {
    all: initial; /* Reset styles */
    position: fixed;
    bottom: 1rem;
    right: 1rem;
    font-family: sans-serif;
    z-index: 9999;
  }

  .chat-icon {
    /* position: absolute; */
    bottom: 3%;
    right: 2%;
    /* background-image: url("./assets/chat2.png"); */
    width: 6rem;
    height: 6rem;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
    box-sizing: border-box;
    transition: all 0.3s ease-in-out;
    position: relative;
  }

  .chat-icon:hover {
    transform: scale(1.05);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
  }

  .chat-dialog {
    position: absolute;
    bottom: 110%;
    right: 50%;
    width: 400px;
    height: 500px;
    background: white;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
    display: flex;
    flex-direction: column;
    overflow: hidden;
  }

  .chat-icon img{
    width: inherit;
  }

  .chat-header {
    background: #4f46e5;
    color: white;
    padding: 0.5rem;
  }

  .chat-body {
    flex: 1;
    padding: 0.5rem;
    overflow-y: auto;
  }
</style>

<svelte:options customElement="chat-widget" />

<div>
  <div class="chat-icon" aria-live="polite" aria-label="Chat" role="button" tabindex="0" on:click={() => (open = !open)} on:keydown={(e) => e.key === "Enter" && (open = !open)}>
    <img src={chatIconUrl} alt="Chat Icon">
  </div>

  {#if open}
    <div class="chat-dialog">
      <div class="chat-header">
        Chat Dialog
      </div>
      <div class="chat-body">
        Hello! How can I assist you today?
      </div>
    </div>
  {/if}
</div>
