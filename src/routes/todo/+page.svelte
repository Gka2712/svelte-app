<script>
	export let name;
	let todoText = "";
	let todos = [];

	function handleClick() {
		if (todoText.trim() != "") {
			todos = [...todos, todoText];
			todoText = "";
		}
	}
    function handleDelete(index){
        todos=todos.filter((_,i)=>i!==index);
    }
</script>
<svelte:head>
	<title>todo</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>
<main>
	<h1>Todo List</h1>
	<input type="text" bind:value={todoText} />
	<button on:click={handleClick}>追加する</button>
	<div class="todolist">
		{#each todos as todo,index (index)}
			<div class="todorecord">
                {todo}
                <button class="delete-button" on:click={()=>handleDelete(index)}>削除</button>
            </div>
		{/each}
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		font-size: 4em;
		font-weight: 100;
	}

	.todorecord {
		font-size: 100%;
		margin-left: 45%;
		margin-top: 2.5%;
		border: 1px solid #333;
		width: 40%;
		min-height:30px;
		word-wrap:break-word;
	}

	.todolist {
		display: flex;
		flex-direction: column;
		margin-top: 1%;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
