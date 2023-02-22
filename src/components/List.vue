<template>
  <ul class="list mt-2">
    <li v-for="(todo, index) in todos" :key="index">
      <div class="flex rounded-full px-4 py-1 my-2 bg-slate-600 text-gray-300 hover:bg-slate-400 hover:text-gray-700">
        <div class="my-auto">
          <span v-if="todo.isDone" class="line-through">{{ todo.activity }}</span>
          <span v-else class="">{{ todo.activity }}</span>
        </div>
        <div class="ml-auto">
          <button @click="doneTodo(index)" class="bg-green-300 rounded-full px-2 py-1 ml-auto my-1 mr-1 text-green-800 hover:bg-green-500 hover:text-green-300">&#128504</button>
          <button @click="deleteTodo(index)" class="bg-red-300 rounded-full px-2 py-1 ml-auto my-1 text-red-700 hover:bg-red-500 hover:text-red-300">&#10005</button>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      default: []
    }
  },
  methods: {
    deleteTodo(index) {
      this.$emit('deleteTodo', index);
    },
    doneTodo(index){
      this.$emit('doneTodo', index);
    }
  }
}
</script>