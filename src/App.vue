<script>
export default {
  data() {
    return {
      isEditing: false,
      todo: "",
      todos: [],
      selectedTodo: null,
    }

  },

  methods: {
    storeTodo() {
      this.todos.push(this.todo);
      this.todo = "";
    },

    removeTodo(index) {
      this.todos.splice(index, 1);
    },

    updateTodo() {
      this.todos.splice(this.selectedIndex, 1, this.todo);
      this.todo = "";
      this.isEditing = false;
    },

    editTodo(index, todo) {
      this.isEditing = true;
      this.todo = todo;
      this.selectedIndex = index;
    },
  },
}
</script>


<template>
  <div id="app" class="container" style="max-width: 500px;margin-top:200px;">
    <h1>Your Todo List</h1>

    <div v-if="!isEditing">
      <input type="text" v-model="todo" style="border:1px solid#039be5" />
      <input
        type="submit"
        value="Add"
        style="background-color:#039be5;border:0;"
        @click="storeTodo"
      />
    </div>
    <div v-else>
      <input type="text" v-model="todo" />
      <input type="submit" value="Update" @click="updateTodo" />
    </div>

    <ol>
      <li v-for="(todo, index) in todos">
        {{ todo }}
        <button
          @click="editTodo(index, todo)"
          style="background-color:#039be5;border:0;"
        >Edit</button>
        <button @click="removeTodo(index)" style="background-color:#039be5;border:0;">Delete</button>
      </li>
    </ol>
  </div>
</template>

<style>
.container {
  max-width: 960px;
  margin: 0 auto;
}
h1 {
  padding-top: 40px;
  color: #039be5;
  text-align: center;
  font-size: 30px;
}
</style>
