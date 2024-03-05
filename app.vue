<template>
  <div>
    <h1>Todoリスト</h1>

    <div>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="deleteTask(index)">削除</button>
        </li>
      </ul>
    </div>

    <form @submit.prevent="addTask">
      <input type="text" v-model="newTask" placeholder="新しいタスクを追加">
      <button type="submit">追加</button>
    </form>
  </div>

</template>

<script setup lang="ts">
// import { useTodoStore } from "pinia";
import { ref } from 'vue';

const tasks = ref<string[]>([]);

const newTask = ref<string>('');

// const todoStore = useTodoStore();

// add task
const addTask = () => {
  if(newTask.value.trim() !== '') {
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
};

// delete task
const deleteTask = (index: number) => {
  tasks.value.splice(index, 1);
};

</script>
