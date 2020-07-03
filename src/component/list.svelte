<script>
  import ListItem from "./listItem.svelte";
  import { flip } from "svelte/animate";
  import { slide } from "svelte/transition";

  export let daftar;
</script>

<style>
  ul {
    list-style-type: none;
    padding: 10px;
  }
  li {
    margin: 0 0 10px;
  }
  h6 {
    text-align: center;
  }
</style>

<ul>
  {#each daftar as item (item.id)}
    <li animate:flip transition:slide>
      <ListItem {item} on:deleteDaftar on:setDone />
    </li>
  {:else}
    <h6>Belum Ada Daftar</h6>
  {/each}
</ul>
