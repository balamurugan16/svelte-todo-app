<script>
	import 'bulma/css/bulma.css';
	import TodoList from "./TodoList.svelte";
	let todos = [
		{
			id: 0,
			item: "Buy eggs"
		},
		{
			id: 1,
			item: "Cook food"
		},
	]
	function keyEnter(event) {
		if (event.key === "Enter")  {
			event.preventDefault();
			document.querySelector(".add-todo").click();
		}
	}
	function addTodo() {
			let todo = document.querySelector("input[type='text']");
			todos = [...todos, {
				id: todos.length,
				item: todo.value
			}]
			todo.value = "";
	}
	function removeTodo(event) {
		todos = todos.filter((todo) => {
			return todo.id !== event.detail.id;
		});
	}
</script>

<style>
	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
</style>

<main>
	<h1>Todo App</h1>
	
	<div>
		<input type="text" placeholder="Enter todo" on:keypress={keyEnter}>
		<button on:click={addTodo} class="add-todo is-primary">
			Add
		</button>
	</div>
	
	<TodoList todos={todos} on:removeTodo={removeTodo}/>
</main>

