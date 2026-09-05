<template>
  <header class="header">
    <div class="main">
        <div class="left">
          <nav class="header-nav">
            <ul class="nav-list">
              <li :class="['nav-item', { active: isActive('/') }]"><a href="#/">HOME</a></li>
              <li :class="['nav-item', { active: isActive('/performance') }]"><a href="#/performance">PERFORMANCE</a></li>
              <li :class="['nav-item', { active: isActive('/listen') }]"><a href="#/listen">LISTEN</a></li>
              <li :class="['nav-item', { active: isActive('/voice') }]"><a href="#/voice">VOICE OF OUR OWN</a></li>
              <li :class="['nav-item', { active: isActive('/contact') }]"><a href="#/contact">CONTACT</a></li>
            </ul>
          </nav>
        </div>

        <div class="right">
          <a href="#/"><img :src="logo" alt="Logo" class="header-logo" /></a>
        </div>
    </div>

  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import logo from '@/assets/images/home/logo.png'

const currentHash = ref(window.location.hash || '#/')

function updateHash() {
  currentHash.value = window.location.hash || '#/'
}

onMounted(() => {
  window.addEventListener('hashchange', updateHash)
})

onBeforeUnmount(() => {
  window.removeEventListener('hashchange', updateHash)
})

function isActive(path) {
  const normalized = currentHash.value.replace(/^#/, '')
  if (path === '/') return normalized === '/' || normalized === ''
  return normalized === path
}
</script>

 

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';
@import '../assets/scss/_common.scss';

.header {
  height: 140px;
  display: flex;
  justify-content: center;
  padding: 12px 5%;
  background-color: #f8f7ef;
}
.main{
  width: 1253px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  display: flex;
}
.nav-list {
  display: flex;
  gap: 20px;
  margin: 0;
  padding: 0;
  list-style: none;
  align-items: center;
}

.nav-item {
  a {
    display: inline-block;
    padding: 6px 12px;
    color: $color-text-dark;
    font-weight: 600;
    font-family: $font-sans;
    text-decoration: none;
    font-size: 0.95rem;
  }

  &.active a {
    background-color: #854529;
    color: $color-white;
    //border-radius: 4px;
    padding: 6px 14px;
  }
}

.header-logo {
  height: 56px;
}

@media (max-width: 768px) {
  .nav-list {
    gap: 10px;
    font-size: 0.9rem;
  }
  .header-logo {
    height: 44px;
  }
}
</style>