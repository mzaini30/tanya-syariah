<script>
  import excalibur from "excalibur-zen";
  import toast from "only-toast";
  import { api, pertanyaan } from "../api";

  let judul;
  let isi;

  async function kirimPertanyaan() {
    const kirim = await excalibur(api, {
      id: pertanyaan,
      kunci: "kirim-pertanyaan",
      judulPertanyaan: judul,
      pertanyaan: isi,
      tanggalBertanya: new Date().toJSON(),
    });
    if (kirim) {
      toast("Pertanyaan berhasil dikirim");
      judul = "";
      isi = "";
    }
  }
</script>

<form
  on:submit|preventDefault={kirimPertanyaan}
  action=""
  class="p-2 grid grid-cols-1 gap-2"
>
  <label for="">Judul Pertanyaan</label>
  <input type="text" bind:value={judul} class="inputan" required />
  <label for="">Isi Pertanyaan</label>
  <textarea
    name=""
    id=""
    cols="30"
    bind:value={isi}
    class="inputan"
    required
    rows="10"
  />
  <div>
    <input
      type="submit"
      value="kirim"
      class="tombol-kirim border-2 border-black px-4 py-2 inline-block"
    />
  </div>
</form>

<style>
  .inputan {
    @apply block border-2 p-1 border-black w-full;
  }
  .tombol-kirim {
    box-shadow: 3px 3px 0 0 black;
  }
</style>
