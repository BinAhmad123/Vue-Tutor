<script setup lang="ts">
import { onUpdated } from 'vue'
import { watch } from 'vue'
import { onMounted } from 'vue'
import { reactive, ref } from 'vue'
const message = ref('Hello World!')
const titleClass = ref('title')
const counter = reactive({ count: 0 })
const id = ref(1)
const list = ref(null)
const input = ref('')
const todoData = ref(null)

async function fetchData() {
  todoData.value = null
  const res = await fetch(`https://jsonplaceholder.typicode.com/todos/${id.value}`)
  todoData.value = await res.json()
  console.log('todoData.value====>', todoData.value, todoData.value.id)
}
// function add() {
//   console.log(typeof list, typeof list.value, list, list.value)
//   list.value.push({ id: id.value++, text: input.value, done: false })
// }
// function remove(x: any) {
//   list.value = list.value.filter((t) => t.id !== x.id)
// }
onMounted(() => {
  //   alert('Mounted')
})
onUpdated(() => {
  //   console.log('list', list.value, typeof )
  //   alert('Updated')
})
fetchData()
watch(id, fetchData)
defineProps<{title?: String}>()
</script>

<template>
  <div>My Work</div>
  <p :class="titleClass">{{ message }}</p>
  <!-- <button @click="add()"></button> -->
  <p>Count is :{{ counter.count }}</p>
  <input type="text" v-model="input" />
  <div v-if="!todoData">Loading...</div>
  <div v-else>
    <input type="checkbox" v-model="todoData.completed" />
    <p :class="{ done: todoData.completed }">
      {{ todoData.title }}
      <!-- <button @click="remove(todoData)"></button> -->
    </p>
  </div>
  <!-- <div v-for="item in list" :key="item.id">
    <input type="checkbox" v-model="item.done" />
    <p :class="{ done: !item.done }">
      {{ item.text }}
      <button @click="remove(item)"></button>
    </p>
  </div> -->
</template>

<style scoped>
.title {
  color: red;
}
.done {
  text-decoration: line-through;
}
</style>
