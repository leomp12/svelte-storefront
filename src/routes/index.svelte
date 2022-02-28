<script context="module">
  let rand;
  export async function load() {
    rand = parseInt(Math.random() * 1000, 10);
    return { maxage: 300 };
  }
</script>

<h1>Welcome to SvelteKit</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<p>rand: {rand}</p>
