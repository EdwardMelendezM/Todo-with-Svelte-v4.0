<script>
  export let todo;
  export let removeTodo;
  export let editById;

  let isEdit = false;
  let formValue = todo.content;

  let inputRef;

  const onDelete=(id)=>{
    removeTodo(id)
  }

  const onEdit=()=>{
    if(isEdit){
      editById(todo.id,formValue)
    }
    isEdit=!isEdit
    if(isEdit){
      inputRef.focus()
      // console.log(inputRef);
    }
    
  }

</script>

<div class="itemTodoContainer">
  {#if !isEdit}
    <div>{todo.content}</div>
  {/if}

    <input
      type="text"
      bind:value={formValue}
      bind:this={inputRef}
      class={`${isEdit?'input ':'hidden_input'}`}
    >

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
  .input{
    padding: 4px;
    border: 0;
    width: 50%;
    border-radius: 6px;
  }
  .hidden_input{
    display: none;
    visibility: hidden;
  }
</style>