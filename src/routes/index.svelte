<script>
  import Header from "$lib/components/Header.svelte";
  import SongItem from "$lib/components/SongItem.svelte";
</script>

<div>
  <div>
    <Header />
  </div>
  <div class="song-item">
    <SongItem />
    <SongItem />
    <SongItem />
    <SongItem />
    <SongItem />
  </div>
</div>

<style>
  .song-item {
    padding: 0.8em;
  }
</style>
