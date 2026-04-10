<template>
  <div id="app">
    <Navbar />
    <router-view />
    <Footer />
    
    <div id="toastContainer" style="
      position: fixed;
      top: 20px;
      right: 20px;
      z-index: 10000;
      display: flex;
      flex-direction: column;
      gap: 10px;
      pointer-events: none;
    "></div>
  </div>
</template>

<script setup>
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'
import { onMounted } from 'vue'

onMounted(() => {
  window.addEventListener('showToast', showToast)
})

const icons = {
  'success': '✅',
  'error': '❌',
  'warning': '⚠️',
  'info': 'ℹ️'
}

const colors = {
  'success': { bg: '#d4edda', text: '#155724', border: '#c3e6cb' },
  'error': { bg: '#f8d7da', text: '#721c24', border: '#f5c6cb' },
  'warning': { bg: '#fff3cd', text: '#856404', border: '#ffeaa7' },
  'info': { bg: '#d1ecf1', text: '#0c5460', border: '#bee5eb' }
}

const showToast = (event) => {
  const { message, type = 'info', duration = 3000 } = event.detail
  const container = document.getElementById('toastContainer')
  
  const toast = document.createElement('div')
  const color = colors[type] || colors['info']
  const icon = icons[type] || icons['info']
  
  toast.innerHTML = `
    <div style="display: flex; align-items: center; gap: 10px;">
      <span style="font-size: 20px;">${icon}</span>
      <span>${message}</span>
    </div>
  `
  
  toast.style.cssText = `
    background: ${color.bg};
    color: ${color.text};
    border: 2px solid ${color.border};
    padding: 12px 20px;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    font-size: 14px;
    font-weight: 500;
    min-width: 250px;
    max-width: 400px;
    pointer-events: auto;
    animation: slideInRight 0.3s ease-out;
    opacity: 1;
  `
  
  container.appendChild(toast)
  
  setTimeout(() => {
    toast.style.animation = 'slideOutRight 0.3s ease-out'
    setTimeout(() => toast.remove(), 300)
  }, duration)
}
</script>

<style>
#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
