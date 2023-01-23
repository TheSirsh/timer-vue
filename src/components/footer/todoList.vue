<template>
  <div class="todoMain">
     <div class="todo">
        <h2 class="todoHead">TodoList</h2>
        <div class="enterActivity">
          <input type="text" class="todoInput" placeholder="Enter ToDo">
          <span class="todoAdd">Add</span>
          </div>
       </div>
       <ul class="todoList"></ul>
  </div>
</template>

<script>
export default {
  data() {
    return {

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

  .todoActivity {
    font-size: calc(100vw / 80);
    list-style: none;
    text-align: left;
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

  .todoInput {
    font-size: calc(100vw / 80);
  }

  .todoInput::placeholder {
    color: grey;
    font-style: italic;
  }
</style>