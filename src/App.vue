
<template>
  <div class="w-screen flex">
    <div class="mx-auto my-8 p-5 border rounded-2xl bg-slate-700">
      <h5 class="text-lg text-gray-300">Simple To Do App</h5>
      <div class="border-y-2 pt-6 pb-2 mt-1 mb-2 border-gray-400">
        <div class="flex items-center py-2 px-2 rounded-full bg-slate-800">
          <input v-model="todo" @keyup.enter="addTodo" type="text" class="focus:outline-none px-2 py-1 bg-transparent placeholder-white text-white hover:placeholde:" placeholder="Input to do">
          <button @click="addTodo" class="bg-sky-600 rounded-full py-1 px-2 text-white ml-2 hover:bg-sky-300 hover:text-gray-500">+</button>
        </div>
        <List :todos="todos" @deleteTodo="deleteTodo" @doneTodo="doneTodo"/>
      </div>
      <small class="text-gray-400 float-right">Total : {{ totalTodo }}</small>
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
      mounted() {
        this.todos = JSON.parse(localStorage.getItem('todos'));
      },  
      computed: {
        totalTodo(){
          return this.todos.length;
        }
      },
      methods: {
        addTodo(){
          this.todos.unshift({
            activity: this.todo,
            isDone: false

          });
          this.todo = "";
          this.saveToLocalStorage(); 
        },
        deleteTodo(todoIndex){
          this.todos = this.todos.filter((item, index)=>{
            if (index != todoIndex) {
              return item;
            }
          })
          this.saveToLocalStorage(); 
        },
        doneTodo(todoIndex){
          this.todos = this.todos.filter((item, index) => {
            if (index == todoIndex) {
              item.isDone = !item.isDone; 
            }

            return item;
          })
          this.saveToLocalStorage(); 
        },
        saveToLocalStorage(){
          localStorage.setItem('todos', JSON.stringify(this.todos))
        }
      }
    }
  </script>