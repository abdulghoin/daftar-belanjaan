<script>
  import { slide } from "svelte/transition";
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  import Header from "../component/header.svelte";
  import FAB from "../component/fab.svelte";

  let judul = "";
  let desc = "";

  const onTambahDaftar = () => {
    dispatch("tambah", { judul, desc });
  };
</script>

<style>
  div {
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 100%;
    position: fixed;
    bottom: 0;
    left: 0;
  }
  form {
    padding: 10px;
    background: navajowhite;
    flex-grow: 2;
  }

  input,
  textarea {
    width: calc(100% - (10px * 2));
    border: none;
    padding: 10px;
    margin: 5px 0;
    border-radius: 8px;
    outline: none;
  }

  textarea {
    height: 100px;
  }
</style>

<div transition:slide={{ duration: 500 }}>
  <Header judul="Tambah Belanjaan" />
  <form on:submit|preventDefault={onTambahDaftar}>
    <input type="text" bind:value={judul} placeholder="Judul" autofocus />
    <textarea bind:value={desc} placeholder="Deskripsi" />
  </form>
</div>
<FAB on:click={onTambahDaftar} type="send" />
