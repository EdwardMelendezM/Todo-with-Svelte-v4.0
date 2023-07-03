<script>
	import Form from '../components/Form.svelte'
  import ItemTodo from '../components/ItemTodo.svelte';
	let listTodo=[]

	const addTodo=(newValue)=>{
		listTodo=[...listTodo, newValue]
	}

	const removeTodo=(id)=>{
		let temp = listTodo.filter((todo)=>todo.id!==id)
		listTodo=[...temp]
	}


	$:console.log(listTodo)
</script>

<svelte:head>
	<title>Todo</title>
	<meta name="Todo application" content="Todo Svelte v4.0" />
</svelte:head>

<div class="container">
	<div class="container_todo">
		<h2>TODO APLICATION</h2>
		<Form addTodo={addTodo}/>
		<div class="container_todos">
				{#each listTodo as todo (todo.id)}
					<ItemTodo
						todo={todo}
						removeTodo={removeTodo}
					/>
				{/each}
		</div>
	</div>
</div>

<style>
	.container{
		height: 100vh;
		width: 100%;
		display: flex;
		align-items: flex-start;
		justify-content: center;
		background-color: #000;
	}
	.container_todo{
		background-color: rgba(255,255,255,0.8);
		max-width: 350px;
		width: auto;
		border-radius: 10px;
		padding: 16px;
		margin-top: 61px;
	}
	.container_todos{
		margin-top: 10px;
	}
</style>
