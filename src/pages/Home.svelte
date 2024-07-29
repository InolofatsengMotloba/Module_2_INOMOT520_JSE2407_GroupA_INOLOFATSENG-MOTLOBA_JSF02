<script>
    import Filter from "../components/Filter.svelte";
    import Sort from "../components/Sort.svelte";
    import ProductList from "../components/Product/ProductList.svelte";
</script>

<style>
    .container {
    display: grid;
    gap: 1rem; 
    column-gap: 12rem;
    margin-top: 0.75rem; 
    margin-left: auto;
    margin-right: auto;
    justify-content: center;
    }

    @media (min-width: 1024px) { 
    .container {
        display: flex;
        align-items: flex-start;
    }
}
</style>

<main>
    <div class="container">
        <Filter />
        <Sort />
    </div>
    <ProductList />
</main>