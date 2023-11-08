<script setup>
import { ref } from 'vue'

let newTask = ref('')
let taskList = ref([
  { text: 'Estudiar', done: false },
  { text: 'Jugar', done: true }
])

function addTask(){
  if(newTask.value.trim() === '')return
  taskList.value.push(
    {
    text: newTask.value,
    done: false
    }
  )
}
newTask.value = ''
</script>

<template>
  <div class="card">
    <h1>Lista de cosas</h1>
    <p class="subtitle">{{ newTask }}</p>
    <div>
      <div v-for="(task, index) in taskList" :key="index" class="task" :class="{ done: task.done }" @keypress.enter="addTask()">{{ task.text }} <span class="button">X</span></div>
    </div>

    <div>
      <input v-model="newTask" type="text" placeholder="Escribe tu tarea" />
      <p class="help" v-show="newTask != ''">Presiona enter para cotinuar</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  background-color: #f7efed;
  max-width: 520px;
  border-radius: 6px;
  padding: 12px 18px;
  margin: 0 auto;
  font-family: 'Roboto', sans-serif;
}

h1 {
  text-transform: uppercase;
  background-color: #beffe9;
  border-radius: 6px;
  text-align: center;
  padding: 0;
  margin: 0;
  margin-bottom: 4px;
}

.subtitle {
  padding: 0;
  margin: 0;
  margin-bottom: 14px;
  text-align: center;
  opacity: 0.6;
}

.task:hover {
  cursor: pointer;
  background-color: hwb(180 20% 14%);
}

.button:hover {
  cursor: pointer;
  background-color: hsl(0, 38%, 49%);
}
.task {
  display: flex;
  justify-content: space-between;
  background-color: #beffe9;
  border-radius: 6px;
  padding: 6px 6px;
  margin-bottom: 2px;
}

.button {
  background-color: #c05d5d;
  padding: 2px 4px;
  border-radius: 4px;
  color: white;
  font-size: 14px;
  line-height: 14px;
}

input {
  width: 100%;
  border: none;
  outline: none;
  padding: 4px 3px;
  border-radius: 6px;
  margin-top: 8px;
}

.help {
  margin: 0;
  margin-top: 2px;
  font-size: 11px;
  opacity: 0.4;
}

.done {
  text-decoration: line-through;
}
</style>
