<template>
  <header class="header">
    <div class="main">
        <div class="left">
          <!-- 手机端折叠菜单按钮（左边） -->
          <button
            class="menu-toggle"
            :class="{ open: menuOpen }"
            aria-label="Toggle menu"
            @click="toggleMenu"
          >
            <span></span>
            <span></span>
            <span></span>
          </button>

          <nav class="header-nav">
            <ul class="nav-list">
              <li :class="['nav-item', { active: isActive('/') }]"><a href="#/">HOME</a></li>
              <li :class="['nav-item', { active: isActive('/performance') }]"><a href="#/performance">PERFORMANCE</a></li>
              <li :class="['nav-item', { active: isActive('/listen') }]"><a href="#/listen">LISTEN</a></li>
              <li :class="['nav-item', { active: isActive('/voice') }]"><a href="#/voice">VOICES OF OUR OWN</a></li>
              <li :class="['nav-item', { active: isActive('/contact') }]"><a href="#/contact">CONTACT</a></li>
            </ul>
          </nav>
        </div>

        <div class="right">
          <a href="#/"><img :src="logo" alt="Logo" class="header-logo" /></a>
        </div>
    </div>

    <!-- 手机端下拉菜单 -->
    <Transition name="mobile-nav">
      <nav v-if="menuOpen" class="mobile-nav">
        <ul class="mobile-nav-list">
          <li :class="{ active: isActive('/') }"><a href="#/" @click="closeMenu">HOME</a></li>
          <li :class="{ active: isActive('/performance') }"><a href="#/performance" @click="closeMenu">PERFORMANCE</a></li>
          <li :class="{ active: isActive('/listen') }"><a href="#/listen" @click="closeMenu">LISTEN</a></li>
          <li :class="{ active: isActive('/voice') }"><a href="#/voice" @click="closeMenu">VOICES OF OUR OWN</a></li>
          <li :class="{ active: isActive('/contact') }"><a href="#/contact" @click="closeMenu">CONTACT</a></li>
        </ul>
      </nav>
    </Transition>
  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import logo from '@/assets/images/home/logo.png'

const currentHash = ref(window.location.hash || '#/')
const menuOpen = ref(false)

function updateHash() {
  currentHash.value = window.location.hash || '#/'
  // 路由切换时收起手机端菜单
  menuOpen.value = false
}

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

function closeMenu() {
  menuOpen.value = false
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
  // performance-detail pages should highlight PERFORMANCE nav
  if (path === '/performance' && normalized.startsWith('/performance-detail')) {
    return true
  }
  // listen-detail pages should highlight LISTEN nav
  if (path === '/listen' && normalized.startsWith('/listen-detail')) {
    return true
  }
  return normalized === path
}
</script>

 

<style lang="scss" scoped>
@import '../assets/scss/_var.scss';
@import '../assets/scss/_common.scss';
@import '../assets/scss/base/_function.scss';

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
  height: 90px;
}

/* 手机端折叠菜单按钮（桌面端隐藏） */
.menu-toggle {
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
  width: 60px;
  height: 60px;
  padding: 0;
  background: none;
  border: none;
  cursor: pointer;

  span {
    display: block;
    width: 44px;
    height: 5px;
    background: #0e0a06;
    border-radius: 3px;
    transition: transform 0.3s ease, opacity 0.3s ease;
  }

  &.open {
    span:nth-child(1) { transform: translateY(15px) rotate(45deg); }
    span:nth-child(2) { opacity: 0; }
    span:nth-child(3) { transform: translateY(-15px) rotate(-45deg); }
  }
}

/* 手机端下拉菜单（桌面端强制隐藏） */
.mobile-nav {
  display: none;
}

@media (min-width: 769px) {
  .mobile-nav { display: none !important; }
}

@media (max-width: 768px) {
  .header {
    height: auto;
    position: relative;
    padding: pxToVw(24) pxToVw(40);
  }

  .main {
    width: 100%;
    justify-content: space-between; /* 左边折叠按钮，右边 logo */
  }

  .header-nav {
    display: none;
  }

  /* 折叠菜单按钮在左边 */
  .menu-toggle {
    display: flex;
    gap: pxToVw(10);

    span {
      width: pxToVw(44);
      height: pxToVw(5);
      border-radius: pxToVw(3);
    }

    &.open {
      span:nth-child(1) { transform: translateY(pxToVw(15)) rotate(45deg); }
      span:nth-child(2) { opacity: 0; }
      span:nth-child(3) { transform: translateY(pxToVw(-15)) rotate(-45deg); }
    }
  }

  /* logo 在右边 */
  .header-logo {
    height: pxToVw(90);
  }

  /* 下拉菜单面板 */
  .mobile-nav {
    display: block;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    z-index: 100;
    background-color: #f8f7ef;
    border-top: 1px solid rgba(14, 10, 6, 0.08);
    box-shadow: 0 pxToVw(16) pxToVw(32) rgba(0, 0, 0, 0.1);
  }

  .mobile-nav-list {
    list-style: none;
    margin: 0;
    padding: pxToVw(20) pxToVw(40) pxToVw(40);
    display: flex;
    flex-direction: column;

    li a {
      display: block;
      padding: pxToVw(26) pxToVw(20);
      color: $color-text-dark;
      font-weight: 600;
      font-family: $font-sans;
      text-decoration: none;
      font-size: pxToVw(30);
      border-bottom: 1px solid rgba(14, 10, 6, 0.06);
    }

    li:last-child a {
      border-bottom: none;
    }

    li.active a {
      background-color: #854529;
      color: #ffffff;
    }
  }
}

/* 下拉菜单过渡动画 */
.mobile-nav-enter-active,
.mobile-nav-leave-active {
  transition: opacity 0.25s ease, transform 0.25s ease;
  transform-origin: top left;
}
.mobile-nav-enter-from,
.mobile-nav-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>