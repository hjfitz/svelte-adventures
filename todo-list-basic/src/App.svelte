<script lang="ts">
	interface Todo {
		done: boolean
		value: string
		id: string
	}
	let todos: Todo[] = []

	let todoVal

	const genRandom = () => Math.random().toString(36).substr(2)

	function addTodo(ev) {
		if (ev.key !== 'Enter') return
		console.log(todoVal)
		todos.push({done: false, value: todoVal, id: genRandom()})
		todos = todos
		todoVal = ''
	}

	function markTodoDone(ev) {
		const {id} = ev.currentTarget.dataset
		const withId = todos.find(todo => todo.id === id)
		withId.done = !withId.done
		todos = todos
	}
</script>

<main>
	<h1>babbys first todo app</h1>

	<section>
		{#each todos as todo}
			<label>
				<input type=checkbox checked={todo.done} on:click={markTodoDone} data-id={todo.id} />
				{todo.value} (done = {todo.done})
			</label>
		{/each}
	</section>


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
