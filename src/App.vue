<template>
  <div id="app">
    <div class="app-title">
      <h1>Shauns' Vue Todos</h1>
    </div>
    <div class="todo-wrapper">
      <div class="todo-container">
        <!-- <TodoList /> -->
        <todo-list :todos="todos" />
        <div class="todo-create-btn-container">
          <todo-create @formSubmitted="createTodo" />
        </div>
      </div>
    </div>
  </div>
</template>

<!-- JS part -->
<script>
import TodoList from '@/components/TodoList'
import TodoCreate from '@/components/TodoCreate'
import store from '@/store'
export default {
  name: 'app',
  components: {
    TodoList, TodoCreate
  },
  data() {
    return {
      todos: store.state.todos
    }
  },
  // This function is run automaticaly by VUE framework
  created() {
    this.todos = store.dispatch('initStore')
  },
  methods: {
    createTodo(todo) {
      store.dispatch('createTodo', todo)
    }
  }
}
</script>

<!-- Stylings, css, scss.... -->
<style lang="scss">
$color-red: #a71d1d;
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.app-title {
  text-align: center;
  color: #5e3a81;
}
.app-error {
  color: #b94040;
}
.app-form {
  .label {
    display: block;
    font-size: 18px;
    font-weight: bold
  }
  .form-input {
    padding: 10px;
    font-size: 17px;
  }
  .form-control {
    margin-bottom: 10px;
    &-last {
      margin-bottom: 0;
    }
  }
}
.is-primary {
  background-color: #37a037 !important;
}
.is-warning {
  background-color: #3695bb !important;
}
.is-danger {
  background-color: #b94040 !important;
}
.app-button {
  font-size: 20px;
  padding: 10px;
  border-radius: 5px;
  text-transform: uppercase;
  letter-spacing: 1px;
  background-color: #5e3a81;
  color: white;
  font-weight: bold;
  text-align: center;
  &:hover {
    cursor: pointer;
  }
}
.todo {
  &-wrapper {
    /* flexible styling */
    display: flex;
    /* it defines alignment along the main axis */
    justify-content: center;
    /*flex-direction: column;*/
    width: 100%;
    /*height: 2000px;*/
  }
  &-create-btn-container {
    margin: 10px;
  }
  &-container {
    display: flex;
    flex-direction: column;
    width: 400px;
    min-height: 200px;
    background-color: #ededed;
    border-radius: 5px;
  }
}
</style>
