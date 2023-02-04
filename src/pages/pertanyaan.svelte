<script>
  import { api, pertanyaan } from "../api";
  import excalibur from "excalibur-zen";

  let data;

  if (localStorage.pertanyaan) {
    data = JSON.parse(localStorage.pertanyaan);
  }

  async function dapatkanListPertanyaan() {
    let datanya = await excalibur(api, {
      id: pertanyaan,
      kunci: "ringkasan",
    });
    datanya = await datanya.json();
    data = datanya;
    localStorage.pertanyaan = JSON.stringify(datanya);
  }
  dapatkanListPertanyaan();
</script>

<a
  href="#/pertanyaan-baru"
  class="border-2 m-2 mt-0 border-black rounded-lg font-bold text-sm px-3 py-1 inline-block"
  >ajukan pertanyaan</a
>
{#if data}
  <div class="p-2 pt-0 grid grid-cols-1 gap-2">
    {#each data as x}
      <a href="#/baca-pertanyaan/{x.id}" class="card border-2 border-black p-2">
        <h2>{x.judulPertanyaan}</h2>
        <p class="text-sm italic">Dijawab oleh {x.yangMenjawab}</p>
      </a>
    {/each}
  </div>
{/if}

<style>
  .card {
    box-shadow: 3px 3px 0 0 black;
  }
</style>
