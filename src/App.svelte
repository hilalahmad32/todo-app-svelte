<script>
	let todos = [];
	let todo = "";
	let error = "";

	const addTodo = () => {
		if (!todo) {
			error = "Please Enter The Todo";
		} else {
			const newTodo = {
				id: Date.now().toString(),
				todo: todo,
			};

			todos = [...todos, newTodo];
			todo = "";
			error = "";
		}
	};

	const deleteTodo = (id) => {
		const newItem = todos.filter((item) => item.id !== id);
		todos = newItem;
	};
	const deleteAllTodo = () => {
		todos = [];
	};
</script>

<main>
	<div class="container">
		<div class="row">
			<div
				class="col-xl-6 col-lg-6 col-md-8 col-sm-12 offset-xl-3 offset-lg-2 offset-md-2 offset-sm-12"
			>
				<div class="card">
					<div class="card-header">
						<h4 class="text-center">Todo App</h4>
					</div>
					<div class="card-body">
						<div class="inline-form">
							<input
								type="text"
								name=""
								id=""
								class="form-control"
								bind:value={todo}
							/>
							<span class="text-danger"
								>{error != "" ? error : ""}</span
							> <br />
							<button
								on:click={addTodo}
								class="btn  mt-2 btn-success">Add</button
							>
						</div>
					</div>
				</div>

				<div class="card">
					<div class="card-body">
						{#if todos.length > 0}
							{#each todos as todo}
								<li
									class="nav-link d-flex justify-content-between"
								>
									<span class="item">{todo.todo}</span>
									<span>
										<button
											on:click={() => deleteTodo(todo.id)}
											class="btn btn-danger"
											>delete</button
										>
									</span>
								</li>
								<hr />
							{/each}
						{:else}
							<h4>Todo Not Found</h4>
						{/if}
					</div>
				</div>
			</div>
		</div>
	</div>
	{#if todos.length > 0}
		<div class=" d-flex justify-content-center">
			<button on:click={deleteAllTodo} class="btn mt-2 btn-danger"
				>Delete All Todo</button
			>
		</div>
	{/if}
</main>

<style>
</style>
