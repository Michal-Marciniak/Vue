<template>
<div>
    <div v-bind:key="todo.id" v-for="todo in todos">
        <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
    </div>
</div>    
</template>

<script>
import TodoItem from './TodoItem';

export default {
    // name to nazwa komponentu
    name: "Todos",
    components: {
            TodoItem
        },
    // todos to wszystkie todos które zwraca aplikacja z App.vue
    props: ["todos"]
}
</script>


<style scoped>

</style>