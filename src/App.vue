<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import Home from './pages/Home.vue'
import Performance from './pages/Performance.vue'
import Listen from './pages/Listen.vue'
import Voice from './pages/Voice.vue'
import Contact from './pages/Contact.vue'

const currentRoute = ref(window.location.hash || '#/')

function resolveView(hash) {
  if (hash === '#/performance') return Performance
  if (hash === '#/listen') return Listen
  if (hash === '#/voice') return Voice
  if (hash === '#/contact') return Contact
  return Home
}

const currentView = ref(resolveView(currentRoute.value))

function onHashChange() {
  currentRoute.value = window.location.hash || '#/'
  currentView.value = resolveView(currentRoute.value)
}

onMounted(() => {
  window.addEventListener('hashchange', onHashChange)
})

onBeforeUnmount(() => {
  window.removeEventListener('hashchange', onHashChange)
})
</script>

<template>
  <div id="app">
    <component :is="currentView" />
  </div>
</template>

<style lang="scss">
@import './assets/scss/_var.scss';
@import './assets/scss/_common.scss';

body {
  margin: 0;
  font-family: 'serif', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: $color-background-light;
}

#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>