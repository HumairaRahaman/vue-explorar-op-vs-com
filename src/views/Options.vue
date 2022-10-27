<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />

    <h3>Our Products {{ todosCount }} Todos!</h3>
    <div>
      <input
        v-model="newTodoName"
        @keyup.enter="addTodo"
        placeholder="Add a List Name"
        type="text"
      />
    </div>
    <div>
      <ul>
        <li v-for="(todo, index) in todos" :key="todo.id">
          <span>{{ todo.name }}</span>
          <button @click="deleteTodo(index)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodoName: "",
      todos: [
        {
          id: 1,
          name: "One",
        },
        {
          id: 2,
          name: "Two",
        },
        {
          id: 3,
          name: "Three",
        },
      ],
      swearewords: ["oil", "sugar", "rice"],
    };
  },
  computed: {
    todosCount() {
      return this.todos.length;
    },
  },
  methods: {
    addTodo() {
      let newTodo = {
        id: Date.now(),
        name: this.newTodoName,
      };
      this.todos.push(newTodo);
      this.newTodoName = "";
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
  watch: {
    newTodoName(newValue) {
      if (this.swearewords.includes(newValue.toLowerCase())) {
        this.newTodoName = "";
        alert("you must NEVER say " + newValue + "!!");
      }
    },
  },
};
</script>

<style>
ul {
  list-style: none;
  padding: 0;
  width: 200px;
  margin: 20px auto 0;
}
li {
  border: 1px solid;
  display: flex;
  margin-bottom: 10px;
}
li span {
  flex-grow: 1;
}
</style>
