<script>
  let name = "";
  let array = [{ name: "Kongthap Phuengsang" }];

  function added() {
    if (!name) return console.error("name undefined");

    array = [...array, { name: name }];
    name = "";
  }

  function remove(index) {
    array = array.filter((n, i) => i !== index);
  }
</script>

<main>
  <h3>Added Name 📚</h3>

  <div class="grid">
    {#each array as rows, index}
      <div>
        {index}
      </div>
      <div class="data">
        {rows.name}
        <span class="remove" on:click={() => remove(index)}>x</span>
      </div>
    {/each}
  </div>

  <form on:submit|preventDefault={added}>
    <input class="input" type="text" bind:value={name} />
    <input class="button" type="submit" value="Add" />
  </form>
</main>

<style>
  .button {
	border: 1px solid black;
	box-shadow: 0px 4px #888888;
    background: white;
  }

  .input{
	box-shadow: 0px 4px #888888;
	border: 1px solid black;
  }

  .data {
    margin-bottom: 5px;
  }
  .grid {
    margin: auto;
    width: 250px;
    display: grid;
    grid-template-columns: 10% 1fr;
  }
  .remove {
    color: rgb(255, 111, 111);
  }
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
</style>
