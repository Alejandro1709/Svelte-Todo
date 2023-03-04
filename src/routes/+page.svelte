<script>
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
	<ul>
		{#each todos as todo}
			<li>
				{#if todo.done}
					<h2 style="text-decoration: line-through;">{todo.title}</h2>
				{:else}
					<h2>{todo.title}</h2>
				{/if}
				<div class="options">
					<button on:click={handleToggle(todo)}>
						{#if todo.done}
							Uncomplete
						{:else}
							Complete
						{/if}
					</button>
					<button on:click={handleDeleteTodo(todo)}>Delete</button>
				</div>
			</li>
		{/each}
	</ul>
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

	h2 {
		font-weight: 400;
	}

	.container {
		font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu,
			Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
		max-width: 800px;
		margin: 0 auto;
	}
	ul {
		display: flex;
		flex-direction: column;
		gap: 1rem;
		list-style: none;
		padding: 0;
		margin: 0;
	}

	li {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 1rem;
		border: 1px solid #eee;
	}

	.options {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
	}

	.options button {
		background: none;
		border: none;
		cursor: pointer;
		color: #333;
		padding: 1rem;
		border-radius: 0.5rem;
		background: #ddd;
	}

	.options button:hover {
		background: #ccc;
	}
</style>
