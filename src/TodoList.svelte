<script>
	import Todo from "./Todo.svelte";
	export let todos;
</script>

<ul>
	{#each todos as {item, id} }
		<Todo item={item} id={id} on:removeTodo/>
	{/each}
</ul>