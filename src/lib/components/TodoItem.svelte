<script>
  import { useTodoState } from "$lib/states/todoState.svelte.js";
  let todoState = useTodoState();
  export let todo;
</script>

<input
  type="checkbox"
  checked={todo.done}
  on:change={() => todoState.changeDone(todo.id)}
  id={todo.id}
/>
<label for={todo.id}>
  {todo.name} ({todo.done ? "done" : "not done"})
</label>
<button on:click={() => todoState.remove(todo.id)}>Remove</button>