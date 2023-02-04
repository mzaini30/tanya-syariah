<script>
  import excalibur from "excalibur-zen";
  import { api, pertanyaan } from "../../api";

  export let params = {};

  let data;

  if (localStorage[`pertanyaan-${params.id}`]) {
    data = JSON.parse(localStorage[`pertanyaan-${params.id}`]);
  }

  async function ambilData() {
    let datanya = await excalibur(api, {
      id: pertanyaan,
      kunci: "tampil",
      idnya: params.id,
    });
    datanya = await datanya.json();
    datanya = datanya[0];
    data = datanya;
    localStorage[`pertanyaan-${params.id}`] = JSON.stringify(datanya);
  }
  ambilData();
</script>

{#if data}
  <div class=" grid grid-cols-1 gap-2 ">
    <h2 class="font-bold p-2 bg-black sticky top-0 text-white text-xl">
      {data.judulPertanyaan}
    </h2>
    <p class="italic px-2 text-sm bg-white">
      Dijawab oleh {data.yangMenjawab}
    </p>
    <p class="p-2  text-sm whitespace-pre-wrap bg-gray-200">
      {data.pertanyaan}
    </p>
    <p class="px-2 pb-2 whitespace-pre-wrap">
      {data.jawaban}
    </p>
  </div>
{/if}
