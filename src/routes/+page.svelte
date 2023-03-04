<script>
	import Todos from '../components/Todos.svelte';
	import { onMount } from 'svelte';

	$: todos = [];

	onMount(async () => {
		const res = await fetch('https://jsonplaceholder.typicode.com/todos');
		todos = await res.json();
	});

	function handleToggle(todo) {
		for (let i = 0; i < todos.length; i++) {
			if (todos[i].id === todo.id) {
				todos[i].done = !todo.done;
			}
		}
	}

	function handleDeleteTodo(todo) {
		todos = todos.filter((t) => t.id !== todo.id);
	}
</script>

<div class="container">
	<Todos {todos} onToggle={handleToggle} onRemove={handleDeleteTodo} />
</div>

<style>
	* {
		padding: 0;
		margin: 0;
	}

	*,
	*::before,
	*::after {
		box-sizing: border-box;
	}
	.container {
		font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
			Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
		max-width: 800px;
		margin: 0 auto;
	}
</style>
