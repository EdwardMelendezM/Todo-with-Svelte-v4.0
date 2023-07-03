<script>
  export let todo;
  export let removeTodo;

  let isEdit = false;
  let formValue = todo.content;

  let inputRef;

  const onDelete=(id)=>{
    removeTodo(id)
  }

  const onEdit=()=>{
    isEdit=!isEdit
    if(inputRef && isEdit){
      setTimeout(() => {
        inputRef.focus()
      },1000);
    }
    console.log(inputRef)
  }

</script>

<div class="itemTodoContainer">
  {#if !isEdit}
    <div>{todo.content}</div>
  {/if}

  {#if isEdit}
    <input
      type="text"
      bind:value={formValue}
      bind:this={inputRef}
    >
  {/if}

  <div>
    <button
      on:click={()=>onEdit()}
    >
      {isEdit ? 'Save':'Edit'}
    </button>
    <button
      on:click={()=>onDelete(todo.id)}
    >
     Delete
    </button>
  </div>
</div>

<style>
  .itemTodoContainer{
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 4px;
  }
  button{
    padding: 4px;
    border: 0;
    border-radius: 10px;
    outline: none;
    cursor: pointer;
  }
  input{
    padding: 4px;
    border: 0;
    width: 50%;
    border-radius: 6px;
  }
</style>