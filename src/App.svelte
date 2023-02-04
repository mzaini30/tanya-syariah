<script>
  // @ts-ignore
  import Router from "svelte-spa-router";
  // @ts-ignore
  import routes from "virtual:generated-pages-svelte";
  import "./tailwind.css";

  let aktif = "artikel";
</script>

<div class="pb-10">
  <h1 class="font-bold text-xl p-2">Tanya Syariah</h1>
  <Router {routes} />
</div>
<div
  class="fixed bottom-0 bagian-menu w-full bg-white border-t-2 border-black grid grid-cols-2"
>
  <a
    href="#/"
    on:click={() => (aktif = "artikel")}
    class={aktif == "artikel" ? "bg-black text-white" : "bg-white text-black"}
    >artikel</a
  >
  <a
    href="#/pertanyaan"
    on:click={() => (aktif = "pertanyaan")}
    class={aktif == "pertanyaan"
      ? "bg-black text-white"
      : "bg-white text-black"}>pertanyaan</a
  >
</div>

<style>
  :global(*) {
    word-wrap: break-word;
  }
  .bagian-menu a {
    @apply p-2 text-sm text-center;
  }
  /* chrome extension */
  /* :global(body) {
    width: 350px;
    height: 500px;
    font-size: 16px;
  } */
</style>
