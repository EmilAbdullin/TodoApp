<template>
  <div>
    <h2>Todo application</h2>
    <AddTodoItem @add-todo="addTodo"/>
    <hr>
    <TodoList
      v-bind:todos="todos"
      @remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import AddTodoItem from '@/components/AddTodoItem.vue'
export default {
  name: 'app',
  data () {
    return {
      todos: []
    }
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos/?_limit=10')
      .then(response => response.json())
      .then(json => {
        this.todos = json
      })
  },
  methods: {
    removeTodo (id) {
      this.todos = this.todos.filter(item => item.id !== id)
    },
    addTodo (item) {
      this.todos.push(item)
    }
  },
  components: {
    TodoList, AddTodoItem
  }
}
</script>
