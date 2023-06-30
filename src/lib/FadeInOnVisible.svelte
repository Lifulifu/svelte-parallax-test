<script>
  import { onMount, onDestroy } from "svelte";

  let thisDom = null;
  let isVisible = false;
  let observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      isVisible = entry.isIntersecting;
    });
  });
  $: visibleClass = isVisible ? "visible" : "";

  onMount(() => {
    observer.observe(thisDom);
  });

  onDestroy(() => {
    observer.unobserve(thisDom);
  });
</script>

<div bind:this={thisDom} class="fade-in-section {visibleClass} {$$props.class}">
  <slot />
</div>

<style>
  .fade-in-section {
    opacity: 0;
    transform: translateY(10vh);
    visibility: hidden;
    transition: opacity 2s cubic-bezier(0, 0, 0, 1), transform 2s cubic-bezier(0, 0, 0, 1);
    will-change: opacity, visibility;
  }
  .fade-in-section.visible {
    opacity: 1;
    transform: none;
    visibility: visible;
  }
</style>
