<script lang="ts">
  import { getContext, createEventDispatcher } from "svelte";
  import { key, type NavBarContext } from "./navbar";

  const dispatch = createEventDispatcher();
  const { hideItemList } = getContext<NavBarContext>(key);

  function onClick() {
    hideItemList();
    dispatch("click");
  }
</script>

<li>
  <button on:click={onClick} class="w-full px-0 py-4 text-white sm:px-6 sm:py-0">
    <slot />
  </button>
</li>
