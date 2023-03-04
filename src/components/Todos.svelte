<script>
	import Todo from './Todo.svelte';

	export let todos;
	export let onToggle;
	export let onRemove;
</script>

<ul>
	{#each todos as todo}
		<Todo {todo} {onToggle} {onRemove} />
	{/each}
</ul>

<style>
	ul {
		display: flex;
		flex-direction: column;
		gap: 1rem;
		list-style: none;
		padding: 0;
		margin: 0;
	}
</style>
