<script lang="ts">
  import { setContext } from "svelte";
  import { fade } from "svelte/transition";
  import { key } from "./navbar";
  export let showItemList: boolean = false;

  let scrollY: number = 0;
  $: isAtPageTop = scrollY < 10;

  function toggleItemList() {
    showItemList = !showItemList;
  }

  function hideItemList() {
    showItemList = false;
  }

  setContext(key, { hideItemList });
</script>

<nav
  class="fixed top-0 z-50 w-full transition-all {isAtPageTop ? 'text-xl' : 'bg-black/50 text-lg'}"
>
  <div class="container flex items-center py-4">
    <div class="mr-auto">
      <slot name="title" />
    </div>

    <!-- horizontal item list -->
    <ul class="hidden sm:flex">
      <slot name="items" />
    </ul>

    <!-- vertical item list toggle -->
    <button class="text-white sm:hidden" on:click={toggleItemList}>
      {showItemList ? "X" : "="}
    </button>
  </div>

  <!-- vertical item list -->
  {#if showItemList}
    <ul transition:fade class="absolute w-full bg-black/70 text-center sm:hidden">
      <slot name="items" />
    </ul>
  {/if}
</nav>

<svelte:window bind:scrollY />
