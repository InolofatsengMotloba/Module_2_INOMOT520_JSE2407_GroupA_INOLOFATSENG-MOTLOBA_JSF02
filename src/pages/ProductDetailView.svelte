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

{#if error}
  <div class="flex justify-center p-5">
    <Error message={error} />
  </div>
{:else if loading}
  <div class="flex justify-center p-5">
    <LoadingCard />
  </div>
{:else}
  <div>
    <a href="/">
        <button class="bg-slate-500" >Back</button>
    </a>
    <img class="object-contain h-48 mt-3" src={product.image}  alt={product.title} />
    <h1>{product.title}</h1>
    <p>{product.description}</p>
    <h2>$ {product.price}</h2>
    <div class="justify-start flex-1">
        <span
        >{product.category}</span>
    </div>
    <p>⭐ {product.rating?.rate}</p>
    <p>reviews: {product.rating?.count}</p>
  </div>
{/if}