<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import LoadingComponent from './components/LoadingComponent.vue'
import ErrorComponent from './components/ErrorComponent.vue'
import MyTransition from './components/MyTransition.vue'
import MyTransition1 from './components/MyTransition1.vue'
import { defineAsyncComponent } from 'vue'
const AsyncComp = defineAsyncComponent({
  loader: () => import('./components/MyWork.vue'),

  loadingComponent: LoadingComponent,

  delay: 200,

  errorComponent: ErrorComponent,

  timeout: 3000
})
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
  <footer>
    <AsyncComp />
    <MyTransition />
    <MyTransition1 />
  </footer>
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
