<template>
    <ul class="list-disc ml-5 mt-2">
        <li v-for="todo in todos" :key="todo">{{ todo }}</li>
    </ul>
</template>

<script>
    export default {
        props: {
            todos:{
                type: Array,
                default: []
            }
        }
    }
</script>