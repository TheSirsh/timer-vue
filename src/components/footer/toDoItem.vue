<template>
  <li class="todoActivity">
    <span v-bind:class="{done: todo.completed}">
      <input type="checkbox"
        v-on:change="todo.completed = !todo.completed">
      {{todo.title}}
    </span>
    <button class="removeToDo"
      v-on:click="$emit('remove-todo', todo.id)"
    >&times;</button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      
    }
  }
}
</script>

<style scoped>
  .todoActivity {
    display: flex;
    justify-content: space-between;
    font-size: calc(100vw / 80);
    list-style: none;
    margin-top: 5px;
    opacity: 0.5;
  }

  .todoActivity:hover {
    cursor: pointer;
    opacity: 1;
  }

  .done {
    text-decoration: line-through;
  }

  .done:hover {
    cursor:  pointer;
    opacity: 1;
  }

</style>