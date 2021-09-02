<script>
	let inventory = ["computer", "tablet", "pen", "mouse", "tv"];
	import { itemsInCart, totalPrice, cartContents } from "./stores.js";
	import Item from "./lib/cart/Item.svelte";
	import { setContext } from "svelte";
	import { extVar, key } from "./external/external.js";
	setContext(key, extVar);
	import { Router, Route, Link } from "svelte-routing";
	import PageA from "./pages/PageA.svelte";
	import PageB from "./pages/PageB.svelte";
	export let url =  "";
</script>
<Router url="{url}">
	<nav>
	   <Link to="PageA">Page A</Link>
	   <Link to="PageB">Page B</Link>
	 </nav>
	 <div>
	   <Route path="PageA" component="{PageA}" /> 
	   <!--for now the router just support case sensitive,
		   one workaround colud be add two time the route
		   Example.
		  <Route path="About" component="{About}" /> 
	   -->
	   <Route path="PageB"><PageB /></Route>
	 </div>
   </Router>
<main>
	<div class="items">
		{#each inventory as item}
			<Item {item} />
		{/each}
	</div>

	<p>There are {$itemsInCart} items in your cart.</p>
	<p>Cart total: ${$totalPrice}</p>
	<p>Cart contents:</p>

	<ol>
		{#each $cartContents as item}
			<li>{item}</li>
		{/each}
	</ol>
</main>

<style>
	.items {
		display: flex;
		flex-direction: row;
	}
</style>
