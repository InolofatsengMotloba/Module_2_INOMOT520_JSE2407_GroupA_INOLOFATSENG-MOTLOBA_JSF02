<script>
  import { onMount } from 'svelte';
  import LoadingCard from '../components/Product/LoadingCard.svelte';
  import Error from '../components/Error.svelte';

  let product = {};
  let error = null;
  let loading = false;

  export let id;

</script>

<main>
    <h1>Products Detailed Page</h1>
</main>