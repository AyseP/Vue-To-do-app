<template>
  <div id="app">
    <input type="text" v-model="name">
    <select v-model="type">
      <option value="highest">Highest</option>
      <option value="high">High</option>
      <option value="low">Low</option>
    </select>
    <button @click="addToDo">Add</button>
    <ul>
      <li v-for="(toDo,index) in toDoList" :key="index">
        {{toDo.name}} - {{toDo.type == "high" ? "!" : "" }}
        <button @click="removetoDo(index)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      name: "",
      type: "high",
      toDoList: []
    };
  },
  components: {},
  methods: {
    addToDo: function() {
      let obj = {
        name: this.name,
        type: this.type
      };
      this.toDoList.push(obj);
    },
    removetoDo: function(index) {
      this.toDoList.splice(index, 1);
    }
  }
};
</script>

