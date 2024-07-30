<script>
  import { onMount } from 'svelte';
  import LoadingCard from "./LoadingCard.svelte";
  import Error from "../Error.svelte";

  let products = [];
  let loading = true;
  let error = null;

  async function getProducts() {
  try {
    let response = await fetch('https://fakestoreapi.com/products');
    if (!response.ok) {
      throw new error("Failed to fetch products");
    }
    products = await response.json();
  } catch (err) {
    error = err.message;
  } finally {
    loading = false;
  }
}

onMount(() => {
  getProducts();
});

</script>

<style></style>

<div>
  {#if loading}
    <LoadingCard />
  {:else if error}
    <Error message={error} />
  {:else if products.length > 0}
    <ul>
      {#each products as product}
        <li>{product.title}</li>
      {/each}
    </ul>
  {:else}
    <p>No products found.</p>
  {/if}
</div>