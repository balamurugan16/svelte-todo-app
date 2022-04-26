<script>
	import { createEventDispatcher } from "svelte";
	const dispatch = createEventDispatcher();
	export let item;
	export let id;
	function removeTodo () {
		dispatch('removeTodo', {
			id: id,
		})
	}
</script>

<div>
	<p>{ item }</p>
	<span class="close is-primary" on:click={removeTodo}>&#10006;</span>
</div>

<style>
	div {
		display:flex;
		align-items:center;
		font-size:14px;
		gap:20px;
		padding:0.5rem;
		border:1px solid black;
	}
	.close {
		cursor:pointer;
		color:red;
	}
</style>