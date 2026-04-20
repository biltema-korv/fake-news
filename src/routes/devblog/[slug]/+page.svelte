<script>
  /** @type {import('./$types').PageData} */
  export let data;
</script>

<article>
  <h1>{data.title}</h1>
  <p>Published: {data.date}</p>
  <p>Effort: {data.effort}</p>
  <svelte:component this={data.content} />
</article>