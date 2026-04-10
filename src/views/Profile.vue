<template>
  <div class="profile-page">
    <section class="profile-section">
      <div class="container">
        <div class="profile-layout">
          <aside class="profile-sidebar">
            <div class="user-card">
              <div class="user-avatar">
                <svg width="100" height="100" viewBox="0 0 100 100">
                  <defs>
                    <linearGradient id="avatarGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                      <stop offset="0%" style="stop-color:#667eea"/>
                      <stop offset="100%" style="stop-color:#764ba2"/>
                    </linearGradient>
                  </defs>
                  <circle cx="50" cy="50" r="50" fill="url(#avatarGrad)"/>
                  <circle cx="50" cy="32" r="14" fill="#fff" opacity=".95"/>
                  <path d="M24 78 Q24 55 50 55 Q76 55 76 78Z" fill="#fff" opacity=".95"/>
                  <polygon points="50,56 46,65 50,63 54,65" fill="#667eea"/>
                  <circle cx="44" cy="30" r="2" fill="#667eea"/>
                  <circle cx="56" cy="30" r="2" fill="#667eea"/>
                  <path d="M44 37 Q50 42 56 37" fill="none" stroke="#667eea" stroke-width="1.5" stroke-linecap="round"/>
                </svg>
              </div>
              <h3>张 同 学</h3>
              <p class="user-email">📧 learner@smartlearn.com</p>
              <div class="user-stats">
                <div class="stat">
                  <span class="stat-value">12</span>
                  <span class="stat-label">已学课程</span>
                </div>
                <div class="stat">
                  <span class="stat-value">186</span>
                  <span class="stat-label">学习天数</span>
                </div>
                <div class="stat">
                  <span class="stat-value">5</span>
                  <span class="stat-label">已获证书</span>
                </div>
              </div>
            </div>

            <nav class="profile-nav">
              <ul>
                <li><a href="#" :class="{ active: activeTab === 'overview' }" @click.prevent="activeTab = 'overview'">📊 学习概览</a></li>
                <li><a href="#" :class="{ active: activeTab === 'courses' }" @click.prevent="activeTab = 'courses'">📚 我的课程</a></li>
                <li><a href="#" :class="{ active: activeTab === 'progress' }" @click.prevent="activeTab = 'progress'">📈 学习进度</a></li>
                <li><a href="#" :class="{ active: activeTab === 'certificates' }" @click.prevent="activeTab = 'certificates'">🏅 我的证书</a></li>
                <li><a href="#" :class="{ active: activeTab === 'settings' }" @click.prevent="activeTab = 'settings'">⚙️ 账户设置</a></li>
              </ul>
            </nav>
          </aside>

          <main class="profile-content">
            <div v-if="activeTab === 'overview'" class="profile-panel active">
              <div class="content-section">
                <h2>学习概览</h2>
                <div class="overview-cards">
                  <div class="overview-card">
                    <div class="card-icon">📚</div>
                    <div class="card-info">
                      <h3>本周学习</h3>
                      <p class="big-number">8.5 <span>小时</span></p>
                      <p class="card-note">↑ 比上周增加 20%</p>
                    </div>
                  </div>
                  <div class="overview-card">
                    <div class="card-icon">🎯</div>
                    <div class="card-info">
                      <h3>完成任务</h3>
                      <p class="big-number">24 <span>个</span></p>
                      <p class="card-note">本月完成进度 75%</p>
                    </div>
                  </div>
                  <div class="overview-card">
                    <div class="card-icon">⭐</div>
                    <div class="card-info">
                      <h3>学习积分</h3>
                      <p class="big-number">2,350 <span>分</span></p>
                      <p class="card-note">排名前 15%</p>
                    </div>
                  </div>
                </div>

                <div class="learning-chart">
                  <h3>近30天学习时长统计</h3>
                  <div class="chart-container">
                    <div class="chart-bar" style="height:60%" title="第1周: 6小时"></div>
                    <div class="chart-bar" style="height:75%" title="第2周: 7.5小时"></div>
                    <div class="chart-bar" style="height:85%" title="第3周: 8.5小时"></div>
                    <div class="chart-bar" style="height:70%" title="第4周: 7小时"></div>
                  </div>
                  <div class="chart-labels">
                    <span>第1周</span><span>第2周</span><span>第3周</span><span>第4周</span>
                  </div>
                </div>
              </div>

              <div class="content-section">
                <h2>学习成就</h2>
                <div class="achievements-grid">
                  <div class="achievement-badge">
                    <div class="badge-icon" style="background:linear-gradient(135deg,#ffd700,#ffed4e)">🏆</div>
                    <h4>初学者</h4>
                    <p>完成第一个课程</p>
                  </div>
                  <div class="achievement-badge">
                    <div class="badge-icon" style="background:linear-gradient(135deg,#c0c0c0,#e8e8e8)">⭐</div>
                    <h4>坚持者</h4>
                    <p>连续学习 30 天</p>
                  </div>
                  <div class="achievement-badge">
                    <div class="badge-icon" style="background:linear-gradient(135deg,#cd7f32,#daa520)">💎</div>
                    <h4>实践者</h4>
                    <p>完成 10 个项目</p>
                  </div>
                  <div class="achievement-badge locked">
                    <div class="badge-icon" style="background:#ccc">🔒</div>
                    <h4>精通者</h4>
                    <p>完成 20 个课程</p>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="activeTab === 'courses'" class="profile-panel active">
              <div class="content-section">
                <h2>我的课程</h2>
                <div class="learning-courses">
                  <div class="learning-course-card" v-for="course in myCourses" :key="course.title">
                    <div class="course-thumbnail" :style="{ background: course.background }">
                      <div v-html="course.illustration"></div>
                    </div>
                    <div class="course-details">
                      <h3>{{ course.title }}</h3>
                      <div class="progress-bar">
                        <div class="progress-fill" :style="{ width: course.progress + '%' }"></div>
                      </div>
                      <div class="progress-info">
                        <span>已完成 {{ course.progress }}%</span>
                        <span>剩余 {{ course.remaining }} 课时</span>
                      </div>
                      <button class="btn btn-primary">继续学习 →</button>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="activeTab === 'progress'" class="profile-panel active">
              <div class="content-section">
                <h2>学习进度</h2>
                <div class="progress-detail-list">
                  <div class="progress-detail-item" v-for="item in progressItems" :key="item.title">
                    <div class="pd-header">
                      <h4>{{ item.title }}</h4>
                      <span class="pd-pct">{{ item.progress }}%</span>
                    </div>
                    <div class="pd-bar">
                      <div class="pd-fill" :style="{ width: item.progress + '%' }"></div>
                    </div>
                    <p class="pd-meta">{{ item.meta }}</p>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="activeTab === 'certificates'" class="profile-panel active">
              <div class="content-section">
                <h2>我的证书</h2>
                <div class="cert-grid">
                  <div class="cert-card" v-for="cert in certificates" :key="cert.title">
                    <div class="cert-banner" :style="{ background: cert.background }">
                      <svg width="200" height="140" viewBox="0 0 200 140">
                        <rect x="20" y="15" width="160" height="110" rx="8" fill="rgba(255,255,255,.15)" stroke="rgba(255,255,255,.4)" stroke-width="1.5"/>
                        <text x="100" y="48" text-anchor="middle" font-size="13" font-weight="bold" fill="white">智慧学习平台</text>
                        <text x="100" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.8)">结业证书</text>
                        <text x="100" y="82" text-anchor="middle" font-size="11" font-weight="bold" fill="white">{{ cert.certTitle }}</text>
                        <circle cx="100" cy="110" r="12" fill="#ffd700"/>
                        <text x="100" y="115" text-anchor="middle" font-size="12" :fill="cert.starColor">★</text>
                      </svg>
                    </div>
                    <div class="cert-body">
                      <h4>{{ cert.title }}</h4>
                      <p>{{ cert.description }}</p>
                      <span class="cert-date">📅 颁发日期：{{ cert.date }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <div v-if="activeTab === 'settings'" class="profile-panel active">
              <div class="content-section">
                <h2>账户设置</h2>
                
                <div class="settings-card">
                  <h3>👤 基本信息</h3>
                  <div class="form-group">
                    <label>用户名</label>
                    <input type="text" v-model="settingsInfo.username" style="max-width:320px">
                  </div>
                  <div class="form-group">
                    <label>邮箱地址</label>
                    <input type="email" v-model="settingsInfo.email" style="max-width:320px">
                  </div>
                  <div class="form-group">
                    <label>手机号码</label>
                    <input type="tel" v-model="settingsInfo.phone" style="max-width:320px">
                  </div>
                  <button class="btn btn-primary" style="margin-top:.5rem">保存修改</button>
                </div>

                <div class="settings-card">
                  <h3>🔔 通知设置</h3>
                  <div class="settings-row">
                    <span class="settings-label">课程更新通知</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="notifications.courseUpdate">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                  <div class="settings-row">
                    <span class="settings-label">学习提醒</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="notifications.studyReminder">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                  <div class="settings-row">
                    <span class="settings-label">新课程推荐</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="notifications.newCourse">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                  <div class="settings-row">
                    <span class="settings-label">活动和优惠推送</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="notifications.promotion">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                </div>

                <div class="settings-card">
                  <h3>🔐 安全设置</h3>
                  <div class="settings-row">
                    <span class="settings-label">登录密码</span>
                    <button class="btn btn-outline btn-small">修改密码</button>
                  </div>
                  <div class="settings-row">
                    <span class="settings-label">两步验证</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="security.twoFactor">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                </div>
              </div>
            </div>
          </main>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const activeTab = ref('overview')

const myCourses = [
  { 
    title: 'Web前端开发全栈课程', 
    progress: 65, 
    remaining: 15, 
    background: 'linear-gradient(135deg,#667eea,#764ba2)', 
    illustration: `<svg width="150" height="100" viewBox="0 0 150 100" style="position:absolute;top:0;left:0;width:100%;height:100%">
      <rect x="10" y="12" width="130" height="76" rx="6" fill="rgba(255,255,255,.15)"/>
      <rect x="10" y="12" width="130" height="18" rx="6" fill="rgba(255,255,255,.25)"/>
      <circle cx="23" cy="21" r="3" fill="#ff6b6b"/>
      <circle cx="33" cy="21" r="3" fill="#ffd166"/>
      <circle cx="43" cy="21" r="3" fill="#06d6a0"/>
      <rect x="20" y="38" width="55" height="4" rx="2" fill="rgba(255,255,255,.7)"/>
      <rect x="20" y="48" width="40" height="4" rx="2" fill="rgba(255,255,255,.5)"/>
      <rect x="20" y="58" width="70" height="4" rx="2" fill="rgba(255,255,255,.7)"/>
      <rect x="20" y="68" width="30" height="4" rx="2" fill="rgba(255,255,255,.5)"/>
      <rect x="85" y="36" width="44" height="48" rx="4" fill="rgba(255,255,255,.12)"/>
      <rect x="90" y="42" width="34" height="3" rx="1" fill="rgba(255,255,255,.6)"/>
      <rect x="90" y="50" width="24" height="3" rx="1" fill="rgba(255,255,255,.4)"/>
      <rect x="90" y="58" width="30" height="3" rx="1" fill="rgba(255,255,255,.6)"/>
    </svg>` 
  },
  { 
    title: 'JavaScript高级编程', 
    progress: 40, 
    remaining: 27, 
    background: 'linear-gradient(135deg,#f093fb,#f5576c)', 
    illustration: `<svg width="150" height="100" viewBox="0 0 150 100" style="position:absolute;top:0;left:0;width:100%;height:100%">
      <text x="32" y="68" font-size="52" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.3)">{</text>
      <text x="98" y="68" font-size="52" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.3)">}</text>
      <text x="58" y="58" font-size="22" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.9)">JS</text>
      <rect x="50" y="65" width="50" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
      <rect x="55" y="73" width="40" height="3" rx="1" fill="rgba(255,255,255,.35)"/>
    </svg>` 
  },
  { 
    title: 'UI/UX设计实战', 
    progress: 80, 
    remaining: 7, 
    background: 'linear-gradient(135deg,#4facfe,#00f2fe)', 
    illustration: `<svg width="150" height="100" viewBox="0 0 150 100" style="position:absolute;top:0;left:0;width:100%;height:100%">
      <rect x="20" y="18" width="65" height="64" rx="5" fill="rgba(255,255,255,.2)"/>
      <rect x="26" y="26" width="53" height="34" rx="3" fill="rgba(255,255,255,.35)"/>
      <rect x="26" y="65" width="25" height="4" rx="2" fill="rgba(255,255,255,.5)"/>
      <rect x="26" y="73" width="40" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
      <circle cx="115" cy="50" r="22" fill="rgba(255,255,255,.18)"/>
      <circle cx="108" cy="42" r="6" fill="#ff6b6b" opacity=".8"/>
      <circle cx="122" cy="42" r="6" fill="#ffd166" opacity=".8"/>
      <circle cx="115" cy="54" r="6" fill="#06d6a0" opacity=".8"/>
      <circle cx="115" cy="50" r="4" fill="white" opacity=".9"/>
    </svg>` 
  }
]

const progressItems = [
  { title: '💻 Web前端开发全栈课程', progress: 65, meta: '已学 28课时 · 剩余 15课时 · 预计 3周完成' },
  { title: '⚡ JavaScript高级编程', progress: 40, meta: '已学 18课时 · 剩余 27课时 · 预计 5周完成' },
  { title: '🎨 UI/UX设计实战', progress: 80, meta: '已学 28课时 · 剩余 7课时 · 预计 1周完成' },
  { title: '🐍 Python数据分析', progress: 15, meta: '已学 6课时 · 剩余 36课时 · 预计 8周完成' },
  { title: '🤖 机器学习入门', progress: 5, meta: '已学 3课时 · 剩余 52课时 · 预计 12周完成' }
]

const certificates = [
  { 
    title: 'HTML5+CSS3 网页开发基础', 
    certTitle: 'HTML5+CSS3网页开发基础',
    description: '全面掌握现代网页开发基础技能', 
    date: '2025-11-10', 
    background: 'linear-gradient(135deg,#667eea,#764ba2)',
    starColor: '#764ba2'
  },
  { 
    title: 'UI/UX 用户体验设计基础', 
    certTitle: 'UI/UX 设计基础',
    description: '掌握用户研究与交互设计方法论', 
    date: '2025-12-25', 
    background: 'linear-gradient(135deg,#4facfe,#00f2fe)',
    starColor: '#0077b6'
  },
  { 
    title: 'Python 编程入门', 
    certTitle: 'Python 编程入门',
    description: '掌握 Python 基础语法与编程思维', 
    date: '2026-01-15', 
    background: 'linear-gradient(135deg,#fa709a,#fee140)',
    starColor: '#c9184a'
  }
]

const settingsInfo = ref({
  username: '张同学',
  email: 'learner@smartlearn.com',
  phone: '138****8888'
})

const notifications = ref({
  courseUpdate: true,
  studyReminder: true,
  newCourse: false,
  promotion: false
})

const security = ref({
  twoFactor: false
})
</script>

<style scoped>
.profile-section {
  padding: 3rem 0;
  background: var(--bg-light);
  min-height: calc(100vh - 200px);
}

.profile-layout {
  display: grid;
  grid-template-columns: 300px 1fr;
  gap: 2rem;
}

.profile-sidebar {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.user-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.user-avatar {
  margin-bottom: 1rem;
}

.user-card h3 {
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.user-email {
  color: var(--text-light);
  font-size: 0.9rem;
  margin-bottom: 1rem;
}

.user-stats {
  display: flex;
  justify-content: space-around;
  padding-top: 1rem;
  border-top: 1px solid var(--border-color);
}

.user-stats .stat {
  text-align: center;
}

.stat-value {
  display: block;
  font-size: 1.5rem;
  font-weight: bold;
  color: var(--primary-color);
}

.stat-label {
  font-size: 0.8rem;
  color: var(--text-light);
}

.profile-nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.profile-nav li {
  border-bottom: 1px solid var(--border-color);
}

.profile-nav li:last-child {
  border-bottom: none;
}

.profile-nav a {
  display: block;
  padding: 1rem 1.5rem;
  color: var(--text-dark);
  text-decoration: none;
  transition: all 0.3s;
}

.profile-nav a:hover,
.profile-nav a.active {
  background: var(--bg-light);
  color: var(--primary-color);
  padding-left: 2rem;
  border-left: 3px solid var(--primary-color);
}

.profile-content {
  background: var(--white);
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.content-section {
  margin-bottom: 2rem;
}

.content-section h2 {
  margin-bottom: 1.5rem;
  color: var(--text-dark);
}

.overview-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
}

.overview-card {
  display: flex;
  gap: 1rem;
  padding: 1.5rem;
  background: var(--bg-light);
  border-radius: 12px;
}

.card-icon {
  font-size: 2.5rem;
}

.big-number {
  font-size: 2rem;
  font-weight: bold;
  color: var(--primary-color);
}

.big-number span {
  font-size: 0.9rem;
  color: var(--text-light);
}

.card-note {
  font-size: 0.85rem;
  color: var(--success-color);
}

.learning-chart {
  margin-top: 2rem;
  background: var(--bg-light);
  padding: 1.5rem;
  border-radius: 12px;
}

.learning-chart h3 {
  margin-bottom: 1rem;
  color: var(--text-dark);
  font-size: 1rem;
}

.chart-container {
  display: flex;
  align-items: flex-end;
  justify-content: space-around;
  height: 150px;
  padding: 0 1rem;
}

.chart-bar {
  width: 60px;
  background: linear-gradient(to top, var(--primary-color), var(--secondary-color));
  border-radius: 8px 8px 0 0;
  transition: height 0.3s;
  cursor: pointer;
}

.chart-bar:hover {
  opacity: 0.8;
}

.chart-labels {
  display: flex;
  justify-content: space-around;
  margin-top: 0.5rem;
  font-size: 0.85rem;
  color: var(--text-light);
}

.achievements-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1.5rem;
}

.achievement-badge {
  text-align: center;
  padding: 1.5rem;
  background: var(--bg-light);
  border-radius: 12px;
}

.achievement-badge.locked {
  opacity: 0.5;
}

.badge-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1rem;
  font-size: 1.5rem;
}

.achievement-badge h4 {
  margin-bottom: 0.3rem;
  color: var(--text-dark);
}

.achievement-badge p {
  font-size: 0.85rem;
  color: var(--text-light);
}

.learning-courses {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.learning-course-card {
  display: flex;
  gap: 1.5rem;
  background: var(--bg-light);
  border-radius: 12px;
  overflow: hidden;
}

.learning-course-card .course-thumbnail {
  width: 150px;
  min-height: 100px;
  position: relative;
  flex-shrink: 0;
}

.learning-course-card .course-details {
  flex: 1;
  padding: 1rem;
}

.learning-course-card h3 {
  font-size: 1.1rem;
  margin-bottom: 0.8rem;
  color: var(--text-dark);
}

.progress-bar {
  height: 8px;
  background: #ddd;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 0.5rem;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
  border-radius: 8px;
}

.progress-info {
  display: flex;
  justify-content: space-between;
  font-size: 0.85rem;
  color: var(--text-light);
  margin-bottom: 1rem;
}

.progress-detail-list {
  display: flex;
  flex-direction: column;
  gap: 1.2rem;
}

.progress-detail-item {
  background: var(--bg-light);
  border-radius: 10px;
  padding: 1rem 1.2rem;
}

.pd-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.6rem;
}

.pd-header h4 {
  font-size: 0.95rem;
  color: var(--text-dark);
}

.pd-pct {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--primary-color);
}

.pd-bar {
  height: 8px;
  background: #ddd;
  border-radius: 8px;
  overflow: hidden;
  margin-bottom: 0.4rem;
}

.pd-fill {
  height: 100%;
  background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
  border-radius: 8px;
}

.pd-meta {
  font-size: 0.8rem;
  color: var(--text-light);
}

.cert-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 1.5rem;
}

.cert-card {
  border: 2px solid var(--border-color);
  border-radius: 12px;
  overflow: hidden;
  transition: transform 0.3s, box-shadow 0.3s;
}

.cert-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
}

.cert-banner {
  height: 140px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.cert-body {
  padding: 1rem 1.2rem 1.2rem;
}

.cert-body h4 {
  margin-bottom: 0.4rem;
  color: var(--text-dark);
  font-size: 1rem;
}

.cert-body p {
  font-size: 0.85rem;
  color: var(--text-light);
  margin-bottom: 0.8rem;
}

.cert-date {
  font-size: 0.8rem;
  color: var(--text-light);
}

.settings-card {
  background: var(--white);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  padding: 1.5rem;
  margin-bottom: 1.5rem;
}

.settings-card h3 {
  font-size: 1.1rem;
  margin-bottom: 1.2rem;
  padding-bottom: 0.6rem;
  border-bottom: 1px solid var(--border-color);
}

.settings-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.7rem 0;
  border-bottom: 1px solid var(--bg-light);
}

.settings-row:last-child {
  border-bottom: none;
}

.settings-label {
  font-size: 0.95rem;
  color: var(--text-dark);
}

.toggle-switch {
  position: relative;
  width: 44px;
  height: 24px;
}

.toggle-switch input {
  opacity: 0;
  width: 0;
  height: 0;
}

.toggle-slider {
  position: absolute;
  inset: 0;
  background: #ccc;
  border-radius: 24px;
  cursor: pointer;
  transition: 0.3s;
}

.toggle-slider::before {
  content: "";
  position: absolute;
  height: 18px;
  width: 18px;
  left: 3px;
  top: 3px;
  background: white;
  border-radius: 50%;
  transition: 0.3s;
}

.toggle-switch input:checked + .toggle-slider {
  background: var(--primary-color);
}

.toggle-switch input:checked + .toggle-slider::before {
  transform: translateX(20px);
}

@media (max-width: 768px) {
  .profile-layout {
    grid-template-columns: 1fr;
  }
  
  .profile-sidebar {
    order: 1;
  }
  
  .learning-course-card {
    flex-direction: column;
  }
  
  .learning-course-card .course-thumbnail {
    width: 100%;
    min-height: 120px;
  }
}
</style>
