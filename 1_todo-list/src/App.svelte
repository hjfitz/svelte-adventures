<script lang="ts">
	import type {Todo} from './types'
	import TodoList from './components/TodoList.svelte'
	
	const storedTodos = JSON.parse(localStorage.getItem('todos')) as Todo[]
	let todos: Todo[] = storedTodos || []

	let todoVal: string

	const genRandom = () => Math.random().toString(36).substr(2)

	function addTodo(ev: KeyboardEvent) {
		if (ev.key !== 'Enter') return
		console.log(todoVal)
		todos.push({done: false, value: todoVal, id: genRandom()})
		todos = todos
		todoVal = ''
	}

	function markTodoDone(ev: MouseEvent) {
		const {id} = (<HTMLInputElement>ev.currentTarget).dataset
		const withId = todos.find(todo => todo.id === id)
		withId.done = !withId.done
		todos = todos
	}

	function saveTodos() {
		const toSave = JSON.stringify(todos)
		localStorage.setItem('todos', toSave)
	}
</script>

<main>
	<h1>babbys first todo app</h1>

	<button on:click={saveTodos}>
		save
	</button>

	<TodoList todos={todos} markTodoDone={markTodoDone} />

	<label>
		<input on:keydown={addTodo} bind:value={todoVal} />
		Add todo
	</label>

</main>

<style>
	h1 {
		margin-top: 0;
	}
</style>
