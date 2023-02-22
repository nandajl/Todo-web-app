
<template>
  <div class="w-screen flex">
    <div class="mx-auto my-8 p-4 border">
      <h5 class="text-lg">Simple To Do App</h5>
      <input v-model="todo" @keyup.enter="addTodo" type="text" class="border-4 rounded-lg mt-3 px-2 py-1">
      <button @click="addTodo" class="bg-zinc-800 rounded-full py-1 px-3 text-white ml-2">+</button>
      <List :todos="todos"/>
    </div>
  </div>
</template>


  <script>
    import List from './components/List.vue'
    export default {
      components: { List },
      data(){
        return {
          todo:"",
          todos: [] 
        }
      },
      methods: {
        addTodo(){
          this.todos.unshift(this.todo);
          this.todo = "";
        }
      }
    }
  </script>