<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  let menuOpen = false;


  function toggleMenu() {
    console.log("Hamburger clicked"); // Debugging line
    menuOpen = !menuOpen;
  }

  function navigate(page) {
    dispatch('navigate', page);
    menuOpen = false;
  }
</script>

<style>
  .navigation {
    position: absolute;
    top: 20px;
    right: 20px;
    z-index: 1002;
  }

  .hamburger {
    cursor: pointer;
    width: 35px;
    height: 30px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    background: transparent;
    border: none;
    z-index: 1001;
  }

  .hamburger div {
    height: 4px;
    width: 30px;
    background-color: #ffffff;
    border-radius: 2px;
  }

  .menu {
    position: absolute;
    top: 30px; /* Positioned below the hamburger */
    right: 0;
    background-color: #ffffff;
    border: 1px solid #000000;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 5px;
    overflow: hidden;
  }

  .menu-item {
    padding: 10px;
    cursor: pointer;
    display: flex;
    align-items: center;
    width: 150px; /* Fixed width for consistency */
    background: none;
    border: none;
    text-align: left;
  }

  .menu-item:hover {
    background-color: #d8d8d8;
  }

  .preview {
    width: 60px;
    height: 60px;
    margin-left: 10px;
    overflow: hidden;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
</style>

<div class="navigation">
  <button type="button" class="hamburger" on:click={toggleMenu}>
    <div></div>
    <div></div>
    <div></div>
  </button>
  {#if menuOpen}
    <div class="menu">
      <button type="button" class="menu-item" on:click={() => navigate('Home')}>
        Home
      </button>
      <button type="button" class="menu-item" on:click={() => navigate('Summaries')}>
        Summaries
      </button>
      <button type="button" class="menu-item" on:click={() => navigate('Notes')}>
        Notes
      </button>
      <button type="button" class="menu-item" on:click={() => navigate('Bookmarks')}>
        Bookmarks
      </button>
      <button type="button" class="menu-item" on:click={() => navigate('Reviews')}>
        Reviews
      </button>
    </div>
  {/if}
</div>