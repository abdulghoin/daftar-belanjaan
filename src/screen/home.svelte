<script>
  import Header from "../component/header.svelte";
  import List from "../component/list.svelte";
  import FAB from "../component/fab.svelte";

  export let daftar;
</script>

<Header />
<List {daftar} on:deleteDaftar on:setDone />
<FAB on:click />
