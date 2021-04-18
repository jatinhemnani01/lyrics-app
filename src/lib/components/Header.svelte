<script>
  import { songs } from "$lib/stores/songs";
  import { loading } from "$lib/stores/loading";
  import Loading from "./Loading.svelte";

  let songName;
  async function getSongs() {
    $loading = true;
    let res = await fetch(`https://api.lyrics.ovh/suggest/${songName}`);
    if (res.ok) {
      let data = await res.json();
      $songs = data.data;
      $loading = false;
    }
  }
</script>

<div class="head-container">
  <form on:submit|preventDefault={getSongs}>
    <!-- svelte-ignore a11y-autofocus -->
    <input
      class="input"
      type="text"
      placeholder="Search Artist, Song, Album"
      autofocus
      bind:value={songName}
    />
    <input class="submit" type="submit" value="Search" />
  </form>
  {#if $loading}
    <Loading />
  {/if}
</div>

<style>
  .head-container {
    background: #e21717;
    height: 40vh;
  }
  form {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }
  .input {
    font-size: 1.2em;
    width: 60%;
    padding: 10px;
    outline: none;
    border: none;
    border-radius: 12px;
    margin: 0 10px;
    max-width: 100%;
    transition: ease 200ms;
  }
  .input:focus {
    border: 3px solid #ffb743;
  }
  .submit {
    font-size: 1.2em;
    border-radius: 12px;
    padding: 10px;
    background: #fff;
    color: crimson;
    font-weight: 400;
  }
  .submit:hover {
    background: #e21717;
    color: white;
    outline: none;
    border: solid;
    transition: ease 200ms;
    border-radius: 15px;
  }

  @media screen and (max-width: 430px) {
    .input {
      padding: 7px;
      margin: 3px;
      font-size: 1em;
    }
    .submit {
      padding: 5px;
      margin: 0px;
      font-size: 1em;
      cursor: pointer;
    }
  }
</style>
