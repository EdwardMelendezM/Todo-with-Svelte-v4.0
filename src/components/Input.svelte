<script>
  export let addTodo;
  export let inputValue = ''
  const onSubmit=(e)=>{
    e.preventDefault()
    if(inputValue.trim().length < 1){
      return;
    }
    let newTodo = {
      id:crypto.randomUUID(),
      content:inputValue
    }
    addTodo(newTodo)
    inputValue=''
    
  }
</script>

<div>
  <form on:submit={onSubmit}>
    <input
    type="text"
    bind:value={inputValue}
    >
    <button type="submit">Agregar</button>
  </form>
</div>