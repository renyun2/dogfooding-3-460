<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <div class="footer-section">
          <h3>智慧学习平台</h3>
          <p>致力于打造最优质的在线学习体验，帮助每个人实现学习目标，提升职业竞争力。</p>
        </div>
        <div class="footer-section">
          <h4>快速链接</h4>
          <ul>
            <li><router-link to="/courses">课程中心</router-link></li>
            <li><router-link to="/plan">学习计划</router-link></li>
            <li><router-link to="/resources">学习资源</router-link></li>
            <li><router-link to="/about">关于我们</router-link></li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>联系我们</h4>
          <ul>
            <li>📧 info@smartlearn.com</li>
            <li>📱 400-888-8888</li>
            <li>📍 北京市朝阳区科技园</li>
          </ul>
        </div>
        <div class="footer-section">
          <h4>关注我们</h4>
          <div class="social-links">
            <a href="#" title="微信" @click.prevent="showToast('📱 正在跳转到微信...')">WeChat</a>
            <a href="#" title="微博" @click.prevent="showToast('📱 正在跳转到微博...')">Weibo</a>
            <a href="#" title="B站" @click.prevent="showToast('📱 正在跳转到B站...')">Bilibili</a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2026 智慧学习平台 版权所有 | 京ICP备12345678号 | 网站地图 | 隐私政策</p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const showToast = (message) => {
  const toastEvent = new CustomEvent('showToast', { 
    detail: { message, type: 'info' } 
  })
  window.dispatchEvent(toastEvent)
}
</script>
