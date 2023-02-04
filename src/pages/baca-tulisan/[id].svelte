<script>
  import excalibur from "excalibur-zen";
  import { api, tulisan } from "../../api";

  export let params = {};

  let data;

  if (localStorage[`tulisan-${params.id}`]) {
    data = JSON.parse(localStorage[`tulisan-${params.id}`]);
  }

  async function ambilData() {
    let datanya = await excalibur(api, {
      id: tulisan,
      kunci: "tampil",
      idnya: params.id,
    });
    datanya = await datanya.json();
    datanya = datanya[0];
    data = datanya;
    localStorage[`tulisan-${params.id}`] = JSON.stringify(datanya);
  }
  ambilData();
</script>

{#if data}
  <div class=" grid grid-cols-1 gap-2">
    <h2 class="font-bold p-2 bg-black sticky top-0 text-white text-xl">
      {data.judul}
    </h2>
    <p class="italic px-2 text-sm">Oleh {data.penulis}</p>
    <p class="px-2 pb-2 whitespace-pre-wrap">
      {data.isi}
    </p>
  </div>
{/if}
