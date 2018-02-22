<template>
  <div class="todo-list">
    <h1>Todos</h1>

    <todo-input v-model="newTodoText"
      @added="addTodo" />
    <ul>
      <todo-item
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @removed="removeTodo" />
    </ul>
  </div>
</template>

<script>
import TodoInput from '@/components/TodoInput'
import TodoItem from '@/components/TodoItem'

let nextTodoId = 1

export default {
  name: 'TodoList',
  components: {
    TodoInput,
    TodoItem
  },
  data () {
    return {
      newTodoText: '',
      todos: [
        {
          id: nextTodoId++,
          checked: true,
          text: 'Study vue basics'
        },
        {
          id: nextTodoId++,
          checked: false,
          text: 'Finish all vue study'
        },
        {
          id: nextTodoId++,
          checked: false,
          text: 'Study tdd'
        },
        {
          id: nextTodoId++,
          checked: false,
          text: 'Study react'
        }
      ]
    }
  },
  methods: {
    addTodo () {
      if (this.newTodoText) {
        this.todos.push({
          id: nextTodoId++,
          checked: false,
          text: this.newTodoText
        })

        this.newTodoText = ''
      }
    },
    removeTodo (id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  display: inline-block;
  list-style-type: none;
  padding: 0;
  max-width: 600px;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
