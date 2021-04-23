<script context="module">
  export const prerender = true;
</script>

<script>
  import Header from "$lib/components/Header.svelte";
  import SongItem from "$lib/components/SongItem.svelte";
  import { songs } from "$lib/stores/songs";
  import Animate from "$lib/components/Animate.svelte";
</script>

<svelte:head>
  <title>Lyrics App</title>
</svelte:head>
<Animate>
  <div>
    <div>
      <Header />
    </div>
    <div class="song-item">
      {#each $songs as item}
        <SongItem title={item.title} artist={item.artist.name} />
      {/each}
    </div>
  </div>
</Animate>

<style>
  .song-item {
    padding: 0.8em;
  }
</style>
