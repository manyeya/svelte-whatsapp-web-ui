<script>
  import { fly } from "svelte/transition";
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  function close() {
    dispatch("close");
  }
  export let title;
</script>

<style>
  .sidebar__left {
    height: 100%;
    width: 30%;
    z-index: 999;
    background-color: whitesmoke;
    position: fixed;
  }

  header {
    background-color: #00bfa5;
    height: calc(100% - 80%);
    width: 100%;
  }

  header .title {
    display: flex;
    flex-direction: row;
    align-items: center;
    color: white;
  }

  header .title i {
    margin: 20% 5%;
    cursor: pointer;
  }

  .content {
    height: calc(100% - 20%);
    width: 100%;
    background-color: rgb(68, 68, 68);
  }
</style>

<div
  in:fly={{opacity:1, x: -600, duration: 500 }}
  out:fly={{opacity:1, x: -1000, duration: 1000 }}
  class="sidebar__left">
  <header>
    <div class="title">
      <i on:click={close} class="material-icons">arrow_back</i>
      <h3>{title}</h3>
    </div>
  </header>
  <div class="content">
    <slot />
  </div>
</div>
