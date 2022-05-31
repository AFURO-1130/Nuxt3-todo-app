<template>
  <div>
    <div class="border" v-for="(todoList, index) in todoLists">
      <input type="checkbox" v-model="todoList.done" />
      <span>{{ todoList.title }}</span>
      <button @click="removeTodo(index)">削除</button>
    </div>
    <input v-model="msg" type="text" />
    <button @click="addTodo()">追加する</button>
  </div>
</template>

<script setup lang="ts">
type Todo = {
  done: boolean;
  title: string;
};

//TODO型定義がまだできてないからそれを配列に割り当てるようにする
const drag = false;
const todoLists = ref([]);
const msg = ref<String>("");
const addTodo = () => {
  todoLists.value.push({
    done: false,
    title: msg.value,
  });
  msg.value = "";
  console.log("todoList", todoLists);
  console.log("msg", msg.value);
};
const removeTodo = (index: number) => {
  todoLists.value.splice(index, 1);
};
</script>

<style>
.border {
  border: solid 1px #111111;
  margin: 5px 0px 5px 0px;
}
</style>
