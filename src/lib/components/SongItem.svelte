<script>
  import { fade } from "svelte/transition";

  export let title;
  export let artist;
</script>

<div in:fade={{ duration: 300 }} class="container">
  <div class="song-info">
    <strong>{artist} -</strong>
    <div class="song">{title}</div>
  </div>
  <div class="lyrics">
    <a
      style="text-decoration: none; color: white;"
      href={"/" + artist + "/" + title}>Get Lyrics</a
    >
  </div>
</div>

<style>
  .container {
    display: flex;
    justify-content: space-between;
    background: #8d3daf;
    align-items: center;
    border-radius: 12px;
    padding: 0.4em;
    margin: 12px 0;
  }
  .song-info {
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }
  .song-info strong {
    font-size: 1.1em;
  }
  .song-info .song {
    font-size: 1.1em;
  }
  .lyrics {
    background-color: #e03b8b;
    border: 0;
    border-radius: 10px;
    color: #fff;
    padding: 5px 10px;
    font-weight: 400;
    cursor: pointer;
  }
</style>
