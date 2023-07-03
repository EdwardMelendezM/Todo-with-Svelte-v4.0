<script>
  export let addTodo;
  let inputValue = ''
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
    placeholder="Ingresar todo"
    bind:value={inputValue}
    class="input_custom"
    >
    <button
      type="submit"
      class="button_custom"
    >Agregar</button>
  </form>
</div>

<style>
  .input_custom{
    padding: 7px 6px;
    border-radius: 6px;
    border: 0;
    outline: none;
  }
  .button_custom{
    padding: 6px;
    background-color: rgba(255,255,255,0.9);
    border-radius: 10px;
    border:0;
    outline: none;
    cursor: pointer;
    &:hover{
      background-color: rgba(255,255,255,0.6);
    }
  }
</style>