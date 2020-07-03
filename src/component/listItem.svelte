<script>
  import { slide } from "svelte/transition";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  export let item = null;

  let isDetailOpen = false;

  const onToggleDetail = () => {
    isDetailOpen = !isDetailOpen;
  };

  const onDeleteDaftar = () => {
    dispatch("deleteDaftar", item.id);
  };

  const onSetDone = () => {
    dispatch("setDone", item.id);
  };
</script>

<style>
  .wrapper {
    background: navajowhite;
    padding: 10px;
    border-radius: 8px;
    transition: all 1s ease;
  }

  .done {
    background: #eee;
  }

  .flex {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  input {
    margin: 0 10px 0 0;
  }

  li:last-of-type {
    margin: 0;
  }

  p {
    margin: 10px 0 0;
  }
</style>

<div class="wrapper {item.isDone ? 'done' : ''}">
  <div class="flex">
    <div class="flex">
      <input type="checkbox" checked={item.isDone} on:change={onSetDone} />
      <h4 on:click={onToggleDetail}>{item.judul}</h4>
    </div>
    <img src="img/delete.svg" alt="delete" on:click={onDeleteDaftar} />
  </div>
  {#if isDetailOpen}
    <p transition:slide>{item.desc}</p>
  {/if}
</div>
