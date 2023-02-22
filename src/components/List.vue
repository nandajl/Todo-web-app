<template>
  <ul class="list mt-2">
    <li v-for="(todo, index) in todos" :key="index">
      <div class="flex">
        <div class="my-auto">
          <span v-if="todo.isDone" class="text-center"><del>{{ todo.activity }}</del></span>
          <span v-else class="text-center">{{ todo.activity }}</span>
        </div>
        <div class="ml-auto">
          <button @click="doneTodo(index)" class="bg-green-600 rounded-full px-2 py-1 ml-auto my-1 mr-1">done</button>
          <button @click="deleteTodo(index)" class="bg-red-600 rounded-full px-2 py-1 ml-auto my-1">x</button>
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