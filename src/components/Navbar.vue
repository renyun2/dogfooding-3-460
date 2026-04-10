<template>
  <nav class="navbar">
    <div class="container">
      <div class="nav-brand">
        <router-link to="/">
          <h1>智慧学习</h1>
        </router-link>
      </div>
      <ul class="nav-menu" :class="{ active: menuOpen }">
        <li><router-link to="/" :class="{ active: $route.path === '/' }">首页</router-link></li>
        <li><router-link to="/courses" :class="{ active: $route.path === '/courses' }">课程中心</router-link></li>
        <li><router-link to="/plan" :class="{ active: $route.path === '/plan' }">学习计划</router-link></li>
        <li><router-link to="/resources" :class="{ active: $route.path === '/resources' }">学习资源</router-link></li>
        <li><router-link to="/profile" :class="{ active: $route.path === '/profile' }">个人中心</router-link></li>
        <li><router-link to="/about" :class="{ active: $route.path === '/about' }">关于我们</router-link></li>
        <li><router-link to="/contact" :class="{ active: $route.path === '/contact' }">联系我们</router-link></li>
      </ul>
      <div class="nav-toggle" @click="toggleMenu" :class="{ active: menuOpen }">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}
</script>

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
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.nav-brand a {
  text-decoration: none;
}

.nav-brand h1 {
  font-size: 1.8rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin: 0;
}

.nav-menu {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
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
    right: 0;
    background: var(--white);
    flex-direction: column;
    padding: 1rem;
    gap: 0;
    box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
    transform: translateY(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s;
  }

  .nav-menu.active {
    transform: translateY(0);
    opacity: 1;
    visibility: visible;
  }

  .nav-menu li {
    padding: 0.8rem 0;
    border-bottom: 1px solid var(--border-color);
  }

  .nav-toggle {
    display: flex;
  }
}
</style>
