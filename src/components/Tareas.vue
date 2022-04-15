<template>
<div>
  <h1>Todo App</h1>
  <label for="">Agregar tareas</label>
  <input type="text" placeholder="Coloque aquí su nueva tarea" v-model="text"> <!-- /*Inyectamos variables de data() */ -->
  <p>La nueva tarea es: {{ text }}</p> <!--/*Prueba de que la variable funciona*/ -->
  <button @click="create">Agregar</button> <!--/*Invocamos métodos. Que están en "methods"  */ -->
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <p>{{todo.text}}</p>
      <button @click="deleteTodo(todo)" style="background-color:red">Eliminar</button>
    </li>
  </ul>
</div>
</template>



<script>
export default
{
  data() /*Variables que ingresa usuario*/
  {
    return{
      id:1,
      todos:[],
      text:''
    }
  },
  methods:{
    restart()
    {
      this.id++
      this.text=''
    },

    create()
    {
      const todo = {
        id:this.id,
        text:this.text
      }
      if(this.text!='')
      {
        this.todos.push(todo)
      }
      this.restart()
    },
    deleteTodo(todo)
    {
      const idx = this.todos.indexOf(todo)
      this.todos.splice(idx,1)
    }
  }
}
</script>
