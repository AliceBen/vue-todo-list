<template>
  <div>
    <button @click="List">列表视图</button>
    <button @click="Shiwang">网络视图</button>
    <ul class="todo-main">
      <Item
        ref="Item"
        v-for="(todo,index) in todos"
        :key="index"
        :todo="todo"
        :index="index"
        :deleteTodo="deleteTodo"
      />
    </ul>
  </div>
</template>

<script>
import Item from "./todoItem";
export default {
  props: {
    todos: Array,
    deleteTodo: Function
  },
  components: {
    //渲染一个组件为动态组件
    Item
  },
  methods: {
    Shiwang() {
      console.log(this.$refs.Item[0]);
      for (let i = 0; i < this.todos.length; i++) {
        this.$refs.Item[i].activeFun();
      }
    },
    List() {
      for (let i = 0; i < this.todos.length; i++) {
        this.$refs.Item[i].defaultFun();
      }
    }
  }
};
</script>

<style scoped>
.todo-main {
  height: 50vh;
  margin-left: 0px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0px;
}

.todo-empty {
  height: 40px;
  line-height: 40px;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding-left: 5px;
  margin-top: 10px;
}
</style>