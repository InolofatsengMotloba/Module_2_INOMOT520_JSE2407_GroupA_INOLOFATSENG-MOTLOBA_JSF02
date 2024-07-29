<script>
  import { Router, Route } from "svelte-routing"
  import Header from "./components/Header.svelte";
  import Home from "./pages/Home.svelte";
  import ProductDetailView from "./pages/ProductDetailView.svelte";
  import Login from "./pages/Login.svelte";
</script>

<Header />
<Router>
  <Route path="/" component={Home} />
  <Route path="products/:id" component={ProductDetailView} />
  <Route path="login" component={Login} />
</Router>
 
<style></style>
