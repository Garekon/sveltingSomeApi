<script>
  import Character from "./lib/character.svelte";
  let characters = [];
  let page = 1;
  async function loadcharacters() {
    const response = await fetch(
      "https://rickandmortyapi.com/api/character?page=" + page
    );
    const data = await response.json();
    console.log(data);
    characters = data.results;
  }

  loadcharacters();

  function nextPage() {
    page++;
    loadcharacters();
  }

  function previusPage() {
    page--;
    loadcharacters();
  }
</script>

<h1 class="title">Rick&Morty API con Svelte</h1>
<div class="btns">
  <button class="btn" on:click={previusPage} disabled={page === 1}
    >Anterior</button
  >
  <button class="btn" on:click={nextPage}>Siguiente</button>
</div>
<div class="container">
  <div class="grid">
    {#each characters as character}
      <Character {character} />
    {/each}
  </div>
</div>
<div class="btns">
  <button class="btn" on:click={previusPage} disabled={page === 1}
    >Anterior</button
  >
  <button class="btn" on:click={nextPage}>Siguiente</button>
</div>

<h4 class="footer">Derechos reservados Garekon©</h4>
