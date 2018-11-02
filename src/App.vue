<template>
  <div id="app">
    <div class="container">
      <h1>Vue Examples</h1>
      <hr>

      <list v-bind:todoItems="groceryList"></list>
      <br>
      <button type="button" class="btn btn-dark" v-on:click="groceryList[2].text = 
        groceryList[2].text === 'bazzzzzzzz' 
        ? 'Whatever else humans are supposed to eat' 
        : 'bazzzzzzzz' ">
        Change it
      </button>
      <hr>

      <div>
        <showInputValue v-bind:input="input"></showInputValue>
        <input v-model="input">
      </div>
      <br>
      <button type="button" class="btn btn-dark" @click="reverseMessage">
        Change it
      </button>
      <hr>

      <div id="todo-list-example">
        <h2>Add a todo</h2>
        <form class="form-inline" v-on:submit.prevent="addNewTodo">
          <div class="form-group mr-sm-3 mb-2">
            <input class="form-control" v-model="newTodoText" id="new-todo" placeholder="E.g. Feed the cat">
          </div>
          <button type="submit" class="btn btn-dark mb-2">Add</button>
        </form>
        <ul class="list-group">
          <todoItemsTemplate class="list-group-item" v-for="(todo, index) in todos" v-bind:key="todo.id" v-bind:title="todo.title" v-on:remove="todos.splice(index, 1)"></todoItemsTemplate>
        </ul>
      </div>
    </div>
    <div style="margin-top: 100px"></div>
  </div>
</template>

<script>
import list from './components/List.vue';
import showInputValue from './components/ShowInputValue.vue';
import todoItemsTemplate from './components/TodoItem.vue';
import store from './store.js';


store.commit('increment')
store.commit('increment')
store.commit('increment')
console.log(store.state.count)

export default {
  name: 'app',
  components: {
    list,
    showInputValue,
    todoItemsTemplate
  },
  data: () => {
    return {
      groceryList: [
        { id: 0, text: 'Vegetables' },
        { id: 1, text: 'Cheese' },
        { id: 2, text: 'Whatever else humans are supposed to eat' }
      ],
      input: 'Hello!!!!!',
      newTodoText: '',
      todos: [
        {
          id: 1,
          title: 'Do the dishes'
        },
        {
          id: 2,
          title: 'Take out the trash'
        },
        {
          id: 3,
          title: 'Mow the lawn'
        }
      ],
      nextTodoId: 4
    };
  },
  methods: {
    reverseMessage: function() {
      this.input = this.input
        .split('')
        .reverse()
        .join('');
    },
    addNewTodo: function() {
      if(this.newTodoText !== '')
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodoText
      });
      this.newTodoText = '';
    }
  }
};
</script>

<style>
#app {
  margin-top: 50px;
}
</style>
