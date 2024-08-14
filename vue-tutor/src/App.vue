<script setup lang="ts">
import { ref, computed } from 'vue'
import Home from './components/Home.vue'
import WorkPlace from './components/WorkPlace.vue'
import NotFound from './components/PageNotFound.vue'

type RouteComponent = {}
type Routes = {
  [key: string]: RouteComponent
}
const routes: Routes = {
  '/': Home,
  '/workplace': WorkPlace
}
const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})
</script>

<template>
  <a href="#/">Home</a> | <a href="#/workplace">WorkPlace</a> |
  <a href="#/non-existent-path">Broken Link</a> 
  <component :is="currentView" />
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
