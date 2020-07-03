<script>
  import Home from "./screen/home.svelte";
  import Form from "./screen/form.svelte";

  const generateID = () => Math.floor(Math.random() * 1000000);

  let daftar = [];
  let isFormOpen = false;

  const toggleForm = () => {
    isFormOpen = !isFormOpen;
  };

  const tambahDaftar = ({ detail }) => {
    toggleForm();
    daftar = [{ ...detail, id: generateID() }, ...daftar];
  };

  const deleteDaftar = ({ detail }) => {
    daftar = daftar.filter(({ id }) => id != detail);
  };

  const setDone = ({ detail: id }) => {
    daftar = daftar.map((item) => {
      if (item.id === id) {
        return { ...item, isDone: !item.isDone };
      }

      return item;
    });
  };
</script>

<Home
  {daftar}
  on:click={toggleForm}
  on:deleteDaftar={deleteDaftar}
  on:setDone={setDone} />

{#if isFormOpen}
  <Form on:click={toggleForm} on:tambah={tambahDaftar} />
{/if}
