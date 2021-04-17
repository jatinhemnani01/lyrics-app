<script>
  import { onMount } from "svelte";
  import { page } from "$app/stores";
  const { artist } = $page.params;
  const { song } = $page.params;
  let lyrics;

  async function getLyrics() {
    let res = await fetch(`https://api.lyrics.ovh/v1/${artist}/${song}`);
    if (res.ok) {
      let data = await res.json();
      lyrics = data.lyrics;
    }
  }
  onMount(() => {
    getLyrics();
  });
</script>

<div class="lyrics">
  <pre>{lyrics}</pre>
</div>

<style>
  .lyrics {
    display: flex;
    text-align: center;
    justify-content: center;
    font-size: 1.4em;
    color: green;
  }
</style>
