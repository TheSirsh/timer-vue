<template>
  <div class="todoMain">
     <div class="todo">
        <h2 class="todoHead">TodoList</h2>
        <form class="enterActivity" @submit.prevent="onSubmit">
          <input type="text" class="todoInput" placeholder="Enter ToDo" v-model="submitTitle">
          <button class="todoAdd">Add</button>
        </form>
       </div>
       <ul class="todoList"
        v-if="todos.length"
      >
        <toDoItem
          v-on:remove-todo="removeTodo" 
          v-for="(todo, i) of todos" :key="todo.id"
          v-bind:todo="todo"
          v-bind:index="i"
        />
       </ul>
       <p v-else>No todos!</p>
  </div>
</template>

<script>
import toDoItem from "@/components/footer/toDoItem.vue";

export default {
  data() {
    return {
      todos: [
        {id: 1, title: "Not completed", completed: false},
        {id: 2, title: "Completed", completed: true},
      ],
      submitTitle: "",
      index: Number,
    }
  },
  components: {
    toDoItem,
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    onSubmit() {
      if (this.submitTitle.trim()) {
        const newTodo = {
          id: 3,
          title: this.submitTitle,
          completed: false,
        }
        this.todos.push(newTodo)
        this.submitTitle = ""
      }
    }
  }
}
</script>

<style scoped>
  .todoHead {
    font-size: calc(100vw / 64);
  }

  .todoMain {
    width: 20%;
    height: 30vh;
    margin: 5px;
  }

  .todoInput {
    opacity: 0.5;
    width: 70%;
  }

  .enterActivity {
    display: flex;
  }

  .todoAdd {
    font-size: calc(100vw / 80);
    background-color: #C5B358;
    border-radius: 5px;
    width: 30%;
  }

  .todoAdd:hover {
    cursor: pointer;
    color: black;
  }

  .todoInput {
    font-size: calc(100vw / 80);
  }

  .todoInput::placeholder {
    color: grey;
    font-style: italic;
  }
</style>