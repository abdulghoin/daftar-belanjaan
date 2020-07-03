<script>
  import { scale } from "svelte/transition";
  export let type = "add";
</script>

<style>
  button {
    border: none;
    background: burlywood;
    width: 54px;
    height: 54px;
    border-radius: 50%;
    position: fixed;
    bottom: 10px;
    right: 10px;
    outline: none;
  }

  button img {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 28px;
  }
</style>

<button on:click transition:scale>
  <img src="img/{type}.svg" alt="{type}-icon" />
</button>
