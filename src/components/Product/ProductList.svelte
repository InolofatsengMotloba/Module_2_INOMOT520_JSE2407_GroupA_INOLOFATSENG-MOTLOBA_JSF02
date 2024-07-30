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

</script>

<style></style>

<main>
    <h1>Product List goes here</h1>
</main>