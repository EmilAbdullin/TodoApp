<template>
  <div>
    <h2>Todo application</h2>
    <router-link to="/">Go to Home</router-link>
    <AddTodoItem @add-todo="addTodo"/>
    <hr>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed"> Completed</option>
      <option value="not-completed"> Not Completed</option>
    </select>
    <Loader v-if="loading"/>
    <TodoList
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos"
      @remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import AddTodoItem from '@/components/AddTodoItem.vue'
import Loader from '@/components/Loader.vue'
export default {
  name: 'app',
  data () {
    return {
      todos: [],
      loading: true,
      filter: 'all'
    }
  },
  mounted () {
    fetch('https://jsonplaceholder.typicode.com/todos/?_limit=10')
      .then(response => response.json())
      .then(json => {
        this.todos = json
        this.loading = false
      })
  },
  computed: {
    filteredTodos: function () {
      if (this.filter === 'all') {
        return this.todos
      }

      if(this.filter === 'completed'){
        return this.todos.filter(item => item.completed)
      }

      if(this.filter === 'not-completed'){
        return this.todos.filter(item => !item.completed)
      }
    }
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
    TodoList, AddTodoItem, Loader
  }
}
</script>
