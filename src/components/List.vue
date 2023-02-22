<template>
  <ul class="list mt-2">
    <li v-for="(todo, index) in todos" :key="index">
      <div class="flex">
        <div class="my-auto">
          <span class="text-center">{{ todo }}</span>
        </div>
        <div class="ml-auto">
          <button @click="deleteTodo(index)" class="bg-red-600 rounded-full px-3 py-1 ml-auto my-1">X</button>
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
      this.$emit('deleteTodo', index)
    }
  }
}
</script>