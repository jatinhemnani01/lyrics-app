<script>
  import Header from "$lib/components/Header.svelte";
  import SongItem from "$lib/components/SongItem.svelte";
  import { songs } from "$lib/stores/songs";
  import Error from "$lib/components/Error.svelte";
</script>

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

<style>
  .song-item {
    padding: 0.8em;
  }
</style>
