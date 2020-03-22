<script>
	import TodoList from './components/TodoList/TodoList.svelte';
	import todoList from './mocks';

</script>

<main>
	<h1>Todo App by SVELTE!</h1>
	<TodoList listTodos={todoList} />
</main>

<style>

</style>
