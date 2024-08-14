<script setup lang="ts">
import { ref, computed } from 'vue'
import { useFetch } from './useFetch'
import { store } from '../store'

const baseUrl = 'https://jsonplaceholder.typicode.com/todos/'
const id = ref('1')
const url = computed(() => baseUrl + id.value)

const { data, error } = useFetch(url)
const retry = () => {
  id.value = ''
  id.value = '1'
}
</script>

<template>
  <button @click="store.count++">Increment</button>
  <br />
  <button @click="store.increment()">Store Increment</button>
  <br />
  <span> Store=>Count:{{ store.count }} </span>
  <br />
  Load post id:
  <button v-for="i in 5" @click="id = `${i}`">{{ i }}</button>

  <div v-if="error">
    <p>Oops! Error encountered: {{ error.message }}</p>
    <button @click="retry">Retry</button>
  </div>
  <div v-else-if="data">
    Data loaded:
    <pre>{{ data }}</pre>
  </div>
  <div v-else>Loading...</div>
</template>
