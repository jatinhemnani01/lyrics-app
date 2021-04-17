<div class="head-container">
  <form>
    <!-- svelte-ignore a11y-autofocus -->
    <input
      class="input"
      type="text"
      placeholder="Search Artist, Song, Album"
      autofocus
    />
    <input class="submit" type="submit" value="Search" />
  </form>
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
