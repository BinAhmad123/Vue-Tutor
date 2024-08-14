<script setup lang="ts">
import HelloWorld from './HelloWorld.vue'
import LoadingComponent from './LoadingComponent.vue'
import ErrorComponent from './ErrorComponent.vue'
import MyTransition from './MyTransition.vue'
import MyTransition1 from './MyTransition1.vue'
import FilterTransition from './FilterTransition.vue'
import MyKeepAlive from './MyKeepAlive.vue'
import { defineAsyncComponent } from 'vue'

const AsyncComp = defineAsyncComponent({
  loader: () => import('./MyWork.vue'),

  loadingComponent: LoadingComponent,

  delay: 200,

  errorComponent: ErrorComponent,

  timeout: 3000
})
</script>

<template>
  <main>
    <p>My Work</p>
    <AsyncComp />
    <br />
    <p>AsyncComp</p>
    <MyTransition />
    <br />
    <p>AsyncComp</p>
    <MyTransition1 />
    <br />
    <p>FilterTransition</p>
    <FilterTransition />
    <br />
    <p>KeepAlive</p>
    <MyKeepAlive />
  </main>
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
