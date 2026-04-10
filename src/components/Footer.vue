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
            <a href="#" title="微信">WeChat</a>
            <a href="#" title="微博">Weibo</a>
            <a href="#" title="B站">Bilibili</a>
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

.footer .container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
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
  padding: 0;
  margin: 0;
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
