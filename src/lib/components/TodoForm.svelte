<script>
  import { useTodoState } from "$lib/states/todoState.svelte.js";
  let todoState = useTodoState();

  const addTodo = (e) => {
    const todo = Object.fromEntries(new FormData(e.target));
    todo.id = crypto.randomUUID();
    todoState.add(todo);
    e.target.reset();
    e.preventDefault();
  };
</script>

<form on:submit|preventDefault={addTodo}>
  <label for="name">Todo</label>
  <input id="name" name="name" type="text" placeholder="Enter a new todo" required />
  <div>
    <input id="done" name="done" type="checkbox" />
    <label for="done">Done</label>
  </div>
  <input type="submit" value="Add Todo" />
</form>