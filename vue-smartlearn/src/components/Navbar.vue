<script setup lang="ts">
import { ref } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const isMenuOpen = ref(false)

const navItems = [
  { name: '首页', path: '/' },
  { name: '课程中心', path: '/courses' },
  { name: '学习计划', path: '/plan' },
  { name: '学习资源', path: '/resources' },
  { name: '个人中心', path: '/profile' },
  { name: '关于我们', path: '/about' },
  { name: '联系我们', path: '/contact' },
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

<template>
  <nav class="navbar">
    <div class="container">
      <div class="nav-brand">
        <h1>智慧学习</h1>
      </div>
      <ul class="nav-menu" :class="{ active: isMenuOpen }" id="navMenu">
        <li v-for="item in navItems" :key="item.path">
          <RouterLink
            :to="item.path"
            :class="{ active: route.path === item.path }"
            @click="closeMenu"
          >
            {{ item.name }}
          </RouterLink>
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

<style scoped>
.navbar {
  background: var(--white);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 1000;
  padding: 1rem 0;
}

.navbar .container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-brand h1 {
  font-size: 1.8rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
}

.nav-menu a {
  text-decoration: none;
  color: var(--text-dark);
  font-weight: 500;
  transition: color 0.3s;
  position: relative;
}

.nav-menu a:hover,
.nav-menu a.active {
  color: var(--primary-color);
}

.nav-menu a.active::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 3px;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  border-radius: 2px;
}

.nav-toggle {
  display: none;
  flex-direction: column;
  cursor: pointer;
  gap: 5px;
}

.nav-toggle span {
  width: 25px;
  height: 3px;
  background: var(--text-dark);
  border-radius: 2px;
  transition: all 0.3s;
}

@media (max-width: 768px) {
  .nav-menu {
    position: fixed;
    top: 70px;
    left: 0;
    width: 100%;
    background: var(--white);
    flex-direction: column;
    padding: 1rem;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    transform: translateY(-150%);
    transition: transform 0.3s;
  }

  .nav-menu.active {
    transform: translateY(0);
  }

  .nav-toggle {
    display: flex;
  }
}
</style>
