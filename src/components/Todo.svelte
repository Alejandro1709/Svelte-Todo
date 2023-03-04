<script>
	export let todo;
	export let onToggle;
	export let onRemove;
</script>

<li>
	{#if todo.done}
		<h2 style="text-decoration: line-through;">{todo.title}</h2>
	{:else}
		<h2>{todo.title}</h2>
	{/if}
	<div class="options">
		<button on:click={onToggle(todo)}>
			{#if todo.done}
				Uncomplete
			{:else}
				Complete
			{/if}
		</button>
		<button on:click={onRemove(todo)}>Delete</button>
	</div>
</li>

<style>
	h2 {
		font-weight: 400;
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
