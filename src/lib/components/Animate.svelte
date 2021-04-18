<script>
  import { fly } from "svelte/transition";
</script>

<div transition:fly={{ duration: 300, x: -300 }}>
  <slot />
</div>
