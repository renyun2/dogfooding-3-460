<script setup lang="ts">
const quickLinks = [
  { name: '课程中心', path: '/courses' },
  { name: '学习计划', path: '/plan' },
  { name: '学习资源', path: '/resources' },
  { name: '关于我们', path: '/about' },
]

const socialLinks = [
  { name: 'WeChat', title: '微信' },
  { name: 'Weibo', title: '微博' },
  { name: 'Bilibili', title: 'B站' },
]
</script>

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
            <li v-for="link in quickLinks" :key="link.path">
              <RouterLink :to="link.path">{{ link.name }}</RouterLink>
            </li>
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
            <a v-for="social in socialLinks" :key="social.name" href="#" :title="social.title">
              {{ social.name }}
            </a>
          </div>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2026 智慧学习平台 版权所有 | 京ICP备12345678号 | 网站地图 | 隐私政策</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--text-dark);
  color: var(--white);
  padding: 3rem 0 1rem;
}

.footer-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-bottom: 2rem;
}

.footer-section h3,
.footer-section h4 {
  margin-bottom: 1rem;
}

.footer-section p {
  color: rgba(255, 255, 255, 0.8);
  line-height: 1.8;
}

.footer-section ul {
  list-style: none;
}

.footer-section ul li {
  margin-bottom: 0.5rem;
}

.footer-section a {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  transition: color 0.3s;
}

.footer-section a:hover {
  color: var(--white);
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-links a {
  padding: 0.5rem 1rem;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 5px;
  transition: background 0.3s;
}

.social-links a:hover {
  background: rgba(255, 255, 255, 0.2);
}

.footer-bottom {
  text-align: center;
  padding-top: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  color: rgba(255, 255, 255, 0.6);
}
</style>
