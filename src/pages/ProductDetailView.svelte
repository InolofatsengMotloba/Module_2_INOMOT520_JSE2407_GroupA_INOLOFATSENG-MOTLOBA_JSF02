<script>
  import { onMount } from 'svelte';
  import LoadingCard from '../components/Product/LoadingCard.svelte';
  import Error from '../components/Error.svelte';

  let product = {};
  let error = null;
  let loading = false;

  export let id;

  // Function to fetch product details
  async function getProductDetails(productId) {
    try {
      const response = await fetch(`https://fakestoreapi.com/products/${productId}`);

      if (!response.ok) {
        throw new error('Network response was not ok');
      }

      const data = await response.json();
      return { response: data, error: null };
    } catch (error) {
      return { response: null, error: error.message };
    }
  }

  onMount(async () => {
    loading = true;
    const { response, error: fetchError } = await getProductDetails(id);
    if (fetchError) {
      error = fetchError;
    } else {
      product = response;
    }
    loading = false;
  });
</script>

<main>
    <h1>Products Detailed Page</h1>
</main>