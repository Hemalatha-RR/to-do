<script>
	let newTodo = '';
	let todos = [];
  
	function addTodo() {
	  if (newTodo.trim() !== '') {
		todos = [...todos, { text: newTodo, completed: false }];
		newTodo = '';
	  }
	}
  
	function toggleTodoCompletion(index) {
	  todos = todos.map((todo, i) => i === index ? { ...todo, completed: !todo.completed } : todo);
	}
  
	function deleteTodo(index) {
	  todos = todos.filter((_, i) => i !== index);
	}
  </script>
  
  <style>
	.completed {
	  text-decoration: line-through;
	}
	.todo-item {
	  display: flex;
	  justify-content: space-between;
	  align-items: center;
	}
	.todo-item button {
	  margin-left: 10px;
	}
  </style>
  
  <main>
	<h1>To-Do List</h1>
	<input bind:value={newTodo} placeholder="What needs to be done?" />
	<button on:click={addTodo}>Add</button>
	<ul>
	  {#each todos as todo, index}
		<li class="todo-item">
		  <span class:completed={todo.completed} on:click={() => toggleTodoCompletion(index)}>
			{todo.text}
		  </span>
		  <button on:click={() => deleteTodo(index)}>Delete</button>
		</li>
	  {/each}
	</ul>
  </main>
  