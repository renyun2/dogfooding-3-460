<template>
  <nav class="navbar">
    <div class="container">
      <div class="nav-brand">
        <h1>智慧学习</h1>
      </div>
      <ul class="nav-menu" :class="{ active: isMenuOpen }">
        <li v-for="item in menuItems" :key="item.path">
          <router-link 
            :to="item.path" 
            :class="{ active: route.path === item.path }"
            @click="closeMenu"
          >
            {{ item.name }}
          </router-link>
        </li>
      </ul>
      <div class="nav-toggle" id="navToggle" @click="toggleMenu">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const isMenuOpen = ref(false)

const menuItems = [
  { path: '/', name: '首页' },
  { path: '/courses', name: '课程中心' },
  { path: '/plan', name: '学习计划' },
  { path: '/resources', name: '学习资源' },
  { path: '/profile', name: '个人中心' },
  { path: '/about', name: '关于我们' },
  { path: '/contact', name: '联系我们' }
]

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  if (window.innerWidth <= 768) {
    isMenuOpen.value = false
  }
}
</script>
