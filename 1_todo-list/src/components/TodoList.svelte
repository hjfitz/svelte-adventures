<script lang="ts">
	import type {Todo} from '../types'
	export let todos: Todo[] = []
	export let markTodoDone: (ev: MouseEvent) => void
</script>

<section>
	{#each todos as todo}
		<label>
			<input 
				type=checkbox 
				checked={todo.done} 
				on:click={markTodoDone} 
				data-id={todo.id} 
			/>
			{todo.value} (done = {todo.done})
		</label>
	{/each}
</section>
