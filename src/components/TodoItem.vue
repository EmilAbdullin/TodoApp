<template>
    <li>
        <span :class="{completed: todo.completed}">
            <input type="checkbox" @change="todo.completed = !todo.completed">
            <strong>{{index + 1}}</strong>
            {{todo.title | uppercase}}
        </span>
        <span>
            <button class="remove-item" @click="$emit('remove-todo',todo.id)">&times;</button>
        </span>
    </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: Number
  },
  filters: {
    uppercase (value) {
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>
li {
    border: 1px solid #ccc;
    display: flex;
    justify-content: space-between;
    padding: .5rem 2rem;
    margin-bottom: 1rem;
}

.remove-item{
    background:oldlace;
    border: none;
    outline: none;
    color:tomato;
    border-radius: 50%;
    width:25px;
    height:25px;
    font-size: 1.5em;
    cursor: pointer;
    font-weight: bold;
}

input{
    margin-right: 1rem;
}

.completed {
    color:#656565;
    text-decoration:line-through;
}

</style>
