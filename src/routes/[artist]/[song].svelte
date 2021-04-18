<script>
  import { onMount } from "svelte";
  import { page } from "$app/stores";
  import Error from "$lib/components/Error.svelte";
  import { lyricsLoading } from "$lib/stores/lyricsLoading";
  import Loading from "$lib/components/Loading.svelte";

  let { artist } = $page.params;
  const { song } = $page.params;
  let lyrics = "";
  let showError = false;

  async function getLyrics() {
    $lyricsLoading = true;
    if (artist === "ZAYN") {
      artist = "Zayn Malik";
    }
    let res = await fetch(`https://api.lyrics.ovh/v1/${artist}/${song}`);
    if (res.ok) {
      let data = await res.json();
      lyrics = data.lyrics;
      showError = false;
      $lyricsLoading = false;
    } else {
      showError = true;
    }
  }
  onMount(() => {
    getLyrics();
  });
</script>

<svelte:head>
  <title>{artist} - {song}</title>
</svelte:head>

<div class="lyrics">
  <pre>{lyrics}</pre>
</div>

{#if showError}
  <Error />
{/if}
{#if $lyricsLoading}
  <Loading />
{/if}

<style>
  .lyrics {
    display: flex;
    text-align: center;
    justify-content: center;
    font-size: 1.4em;
    color: green;
  }
  .lyrics pre {
    background: #e21717;
    color: white;
    padding: 1em;
    overflow: auto;
  }
</style>
