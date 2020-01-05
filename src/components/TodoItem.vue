<template>
    <li>
        <span>
            <input type="checkbox">
            <strong>{{todo.id}}</strong>
            {{todo.title}}
        </span>
        <span><button class="remove-item">&times;</button></span>
    </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
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
}

</style>
