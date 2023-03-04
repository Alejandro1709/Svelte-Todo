<script>
	import Todos from '../components/Todos.svelte';

	$: todos = [
		{ id: 1, title: 'Clean My Room', done: false },
		{ id: 2, title: 'Watch a movie', done: false },
		{ id: 3, title: 'Drink Soda', done: true },
		{ id: 4, title: 'Finish summer course', done: true }
	];

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
