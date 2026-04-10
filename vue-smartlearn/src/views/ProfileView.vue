<script setup lang="ts">
import { ref } from 'vue'

const activeTab = ref('overview')

const tabs = [
  { id: 'overview', name: '📊 学习概览' },
  { id: 'courses', name: '📚 我的课程' },
  { id: 'progress', name: '📈 学习进度' },
  { id: 'certificates', name: '🏅 我的证书' },
  { id: 'settings', name: '⚙️ 账户设置' },
]

const userStats = [
  { value: 12, label: '已学课程' },
  { value: 186, label: '学习天数' },
  { value: 5, label: '已获证书' },
]

const overviewCards = [
  { icon: '📚', title: '本周学习', value: '8.5', unit: '小时', note: '↑ 比上周增加 20%' },
  { icon: '🎯', title: '完成任务', value: '24', unit: '个', note: '本月完成进度 75%' },
  { icon: '⭐', title: '学习积分', value: '2,350', unit: '分', note: '排名前 15%' },
]

const achievements = [
  { icon: '🏆', title: '初学者', desc: '完成第一个课程', bg: 'linear-gradient(135deg,#ffd700,#ffed4e)', locked: false },
  { icon: '⭐', title: '坚持者', desc: '连续学习 30 天', bg: 'linear-gradient(135deg,#c0c0c0,#e8e8e8)', locked: false },
  { icon: '💎', title: '实践者', desc: '完成 10 个项目', bg: 'linear-gradient(135deg,#cd7f32,#daa520)', locked: false },
  { icon: '🔒', title: '精通者', desc: '完成 20 个课程', bg: '#ccc', locked: true },
]

const myCourses = [
  { 
    title: 'Web前端开发全栈课程', 
    progress: 65, 
    remaining: 15,
    bg: 'linear-gradient(135deg,#667eea,#764ba2)',
    svgType: 'frontend'
  },
  { 
    title: 'JavaScript高级编程', 
    progress: 40, 
    remaining: 27,
    bg: 'linear-gradient(135deg,#f093fb,#f5576c)',
    svgType: 'js'
  },
  { 
    title: 'UI/UX设计实战', 
    progress: 80, 
    remaining: 7,
    bg: 'linear-gradient(135deg,#4facfe,#00f2fe)',
    svgType: 'design'
  },
]

const progressList = [
  { title: '💻 Web前端开发全栈课程', pct: 65, learned: 28, remaining: 15, weeks: 3 },
  { title: '⚡ JavaScript高级编程', pct: 40, learned: 18, remaining: 27, weeks: 5 },
  { title: '🎨 UI/UX设计实战', pct: 80, learned: 28, remaining: 7, weeks: 1 },
  { title: '🐍 Python数据分析', pct: 15, learned: 6, remaining: 36, weeks: 8 },
  { title: '🤖 机器学习入门', pct: 5, learned: 3, remaining: 52, weeks: 12 },
]

const certificates = [
  { title: 'HTML5+CSS3 网页开发基础', desc: '全面掌握现代网页开发基础技能', date: '2025-11-10', bg: 'linear-gradient(135deg,#667eea,#764ba2)' },
  { title: 'UI/UX 用户体验设计基础', desc: '掌握用户研究与交互设计方法论', date: '2025-12-25', bg: 'linear-gradient(135deg,#4facfe,#00f2fe)' },
  { title: 'Python 编程入门', desc: '掌握 Python 基础语法与编程思维', date: '2026-01-15', bg: 'linear-gradient(135deg,#fa709a,#fee140)' },
]

const settings = {
  notifications: {
    courseUpdate: true,
    studyReminder: true,
    newCourse: false,
    promotion: false,
  },
  security: {
    twoFactor: true,
  }
}
</script>

<template>
  <div class="profile-page">
    <section class="profile-section">
      <div class="container">
        <div class="profile-layout">
          <!-- 侧边栏 -->
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
                <div v-for="stat in userStats" :key="stat.label" class="stat">
                  <span class="stat-value">{{ stat.value }}</span>
                  <span class="stat-label">{{ stat.label }}</span>
                </div>
              </div>
            </div>

            <nav class="profile-nav">
              <ul>
                <li v-for="tab in tabs" :key="tab.id">
                  <a 
                    href="#" 
                    :class="['profile-tab', { active: activeTab === tab.id }]"
                    @click.prevent="activeTab = tab.id"
                  >
                    {{ tab.name }}
                  </a>
                </li>
              </ul>
            </nav>
          </aside>

          <!-- 主内容区 -->
          <main class="profile-content">
            <!-- 学习概览 -->
            <div v-if="activeTab === 'overview'" class="profile-panel">
              <div class="content-section">
                <h2>学习概览</h2>
                <div class="overview-cards">
                  <div v-for="card in overviewCards" :key="card.title" class="overview-card">
                    <div class="card-icon">{{ card.icon }}</div>
                    <div class="card-info">
                      <h3>{{ card.title }}</h3>
                      <p class="big-number">{{ card.value }} <span>{{ card.unit }}</span></p>
                      <p class="card-note">{{ card.note }}</p>
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
                  <div v-for="badge in achievements" :key="badge.title" class="achievement-badge" :class="{ locked: badge.locked }">
                    <div class="badge-icon" :style="{ background: badge.bg }">{{ badge.icon }}</div>
                    <h4>{{ badge.title }}</h4>
                    <p>{{ badge.desc }}</p>
                  </div>
                </div>
              </div>
            </div>

            <!-- 我的课程 -->
            <div v-if="activeTab === 'courses'" class="profile-panel">
              <div class="content-section">
                <h2>我的课程</h2>
                <div class="learning-courses">
                  <div v-for="course in myCourses" :key="course.title" class="learning-course-card">
                    <div class="course-thumbnail" :style="{ background: course.bg }">
                      <!-- SVG 插图 -->
                      <svg v-if="course.svgType === 'frontend'" width="150" height="100" viewBox="0 0 150 100">
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
                      </svg>
                      <svg v-else-if="course.svgType === 'js'" width="150" height="100" viewBox="0 0 150 100">
                        <text x="32" y="68" font-size="52" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.3)">{</text>
                        <text x="98" y="68" font-size="52" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.3)">}</text>
                        <text x="58" y="58" font-size="22" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.9)">JS</text>
                        <rect x="50" y="65" width="50" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
                        <rect x="55" y="73" width="40" height="3" rx="1" fill="rgba(255,255,255,.35)"/>
                      </svg>
                      <svg v-else-if="course.svgType === 'design'" width="150" height="100" viewBox="0 0 150 100">
                        <rect x="20" y="18" width="65" height="64" rx="5" fill="rgba(255,255,255,.2)"/>
                        <rect x="26" y="26" width="53" height="34" rx="3" fill="rgba(255,255,255,.35)"/>
                        <rect x="26" y="65" width="25" height="4" rx="2" fill="rgba(255,255,255,.5)"/>
                        <rect x="26" y="73" width="40" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
                        <circle cx="115" cy="50" r="22" fill="rgba(255,255,255,.18)"/>
                        <circle cx="108" cy="42" r="6" fill="#ff6b6b" opacity=".8"/>
                        <circle cx="122" cy="42" r="6" fill="#ffd166" opacity=".8"/>
                        <circle cx="115" cy="54" r="6" fill="#06d6a0" opacity=".8"/>
                        <circle cx="115" cy="50" r="4" fill="white" opacity=".9"/>
                      </svg>
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

            <!-- 学习进度 -->
            <div v-if="activeTab === 'progress'" class="profile-panel">
              <div class="content-section">
                <h2>学习进度</h2>
                <div class="progress-detail-list">
                  <div v-for="item in progressList" :key="item.title" class="progress-detail-item">
                    <div class="pd-header">
                      <h4>{{ item.title }}</h4>
                      <span class="pd-pct">{{ item.pct }}%</span>
                    </div>
                    <div class="pd-bar"><div class="pd-fill" :style="{ width: item.pct + '%' }"></div></div>
                    <p class="pd-meta">已学 {{ item.learned }}课时 · 剩余 {{ item.remaining }}课时 · 预计 {{ item.weeks }}周完成</p>
                  </div>
                </div>
              </div>
            </div>

            <!-- 我的证书 -->
            <div v-if="activeTab === 'certificates'" class="profile-panel">
              <div class="content-section">
                <h2>我的证书</h2>
                <div class="cert-grid">
                  <div v-for="cert in certificates" :key="cert.title" class="cert-card">
                    <div class="cert-banner" :style="{ background: cert.bg }">
                      <svg width="200" height="140" viewBox="0 0 200 140">
                        <rect x="20" y="15" width="160" height="110" rx="8" fill="rgba(255,255,255,.15)" stroke="rgba(255,255,255,.4)" stroke-width="1.5"/>
                        <text x="100" y="48" text-anchor="middle" font-size="13" font-weight="bold" fill="white">智慧学习平台</text>
                        <text x="100" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.8)">结业证书</text>
                        <text x="100" y="82" text-anchor="middle" font-size="11" font-weight="bold" fill="white">{{ cert.title }}</text>
                        <circle cx="100" cy="110" r="12" fill="#ffd700"/>
                        <text x="100" y="115" text-anchor="middle" font-size="12" fill="#764ba2">★</text>
                      </svg>
                    </div>
                    <div class="cert-body">
                      <h4>{{ cert.title }}</h4>
                      <p>{{ cert.desc }}</p>
                      <span class="cert-date">📅 颁发日期：{{ cert.date }}</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <!-- 账户设置 -->
            <div v-if="activeTab === 'settings'" class="profile-panel">
              <div class="content-section">
                <h2>账户设置</h2>

                <div class="settings-card">
                  <h3>👤 基本信息</h3>
                  <div class="form-group">
                    <label>用户名</label>
                    <input type="text" value="张同学" style="max-width:320px">
                  </div>
                  <div class="form-group">
                    <label>邮箱地址</label>
                    <input type="email" value="learner@smartlearn.com" style="max-width:320px">
                  </div>
                  <div class="form-group">
                    <label>手机号码</label>
                    <input type="tel" value="138****8888" style="max-width:320px">
                  </div>
                  <button class="btn btn-primary" style="margin-top:.5rem">保存修改</button>
                </div>

                <div class="settings-card">
                  <h3>🔔 通知设置</h3>
                  <div class="settings-row">
                    <span class="settings-label">课程更新通知</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="settings.notifications.courseUpdate">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                  <div class="settings-row">
                    <span class="settings-label">学习提醒</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="settings.notifications.studyReminder">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                  <div class="settings-row">
                    <span class="settings-label">新课程推荐</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="settings.notifications.newCourse">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                  <div class="settings-row">
                    <span class="settings-label">活动和优惠推送</span>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="settings.notifications.promotion">
                      <span class="toggle-slider"></span>
                    </label>
                  </div>
                </div>

                <div class="settings-card">
                  <h3>🔒 安全设置</h3>
                  <div class="settings-row">
                    <div>
                      <span class="settings-label">登录密码</span>
                      <p class="settings-value">上次修改：2025-12-01</p>
                    </div>
                    <button class="btn btn-secondary btn-small">修改密码</button>
                  </div>
                  <div class="settings-row">
                    <div>
                      <span class="settings-label">两步验证</span>
                      <p class="settings-value">通过手机短信验证</p>
                    </div>
                    <label class="toggle-switch">
                      <input type="checkbox" v-model="settings.security.twoFactor">
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

<style scoped>
.profile-section {
  padding: 3rem 0;
  background: var(--light-bg);
  min-height: calc(100vh - 200px);
}

.profile-layout {
  display: flex;
  gap: 2rem;
}

.profile-sidebar {
  width: 280px;
  flex-shrink: 0;
}

.user-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  text-align: center;
  margin-bottom: 1.5rem;
}

.user-avatar {
  width: 100px;
  height: 100px;
  margin: 0 auto 1rem;
  border-radius: 50%;
  overflow: hidden;
}

.user-card h3 {
  color: var(--text-dark);
  margin-bottom: 0.5rem;
}

.user-email {
  color: var(--text-light);
  font-size: 0.9rem;
  margin-bottom: 1.5rem;
}

.user-stats {
  display: flex;
  justify-content: space-around;
  padding-top: 1.5rem;
  border-top: 1px solid #eee;
}

.stat {
  text-align: center;
}

.stat-value {
  display: block;
  font-size: 1.5rem;
  font-weight: bold;
  color: var(--primary-color);
}

.stat-label {
  font-size: 0.85rem;
  color: var(--text-light);
}

.profile-nav {
  background: var(--white);
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  overflow: hidden;
}

.profile-nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.profile-tab {
  display: block;
  padding: 1rem 1.5rem;
  color: var(--text-dark);
  text-decoration: none;
  transition: all 0.3s;
  border-left: 3px solid transparent;
}

.profile-tab:hover {
  background: var(--light-bg);
  color: var(--primary-color);
}

.profile-tab.active {
  background: var(--light-bg);
  color: var(--primary-color);
  border-left-color: var(--primary-color);
  padding-left: 2rem;
}

.profile-content {
  flex: 1;
}

.content-section {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  margin-bottom: 2rem;
}

.content-section h2 {
  color: var(--text-dark);
  margin-bottom: 1.5rem;
  font-size: 1.5rem;
}

.overview-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.overview-card {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.5rem;
  background: var(--light-bg);
  border-radius: 12px;
}

.card-icon {
  font-size: 2.5rem;
}

.card-info h3 {
  font-size: 0.9rem;
  color: var(--text-light);
  margin-bottom: 0.3rem;
}

.big-number {
  font-size: 2rem;
  font-weight: bold;
  color: var(--primary-color);
  margin-bottom: 0.3rem;
}

.big-number span {
  font-size: 1rem;
  font-weight: normal;
  color: var(--text-light);
}

.card-note {
  font-size: 0.85rem;
  color: #06d6a0;
}

.learning-chart {
  margin-top: 2rem;
}

.learning-chart h3 {
  margin-bottom: 1rem;
  color: var(--text-dark);
}

.chart-container {
  display: flex;
  align-items: flex-end;
  justify-content: space-around;
  height: 200px;
  background: var(--light-bg);
  padding: 1.5rem;
  border-radius: 12px;
  gap: 1rem;
}

.chart-bar {
  width: 60px;
  background: linear-gradient(to top, var(--primary-color), var(--secondary-color));
  border-radius: 8px 8px 0 0;
  transition: opacity 0.3s;
}

.chart-bar:hover {
  opacity: 0.8;
}

.chart-labels {
  display: flex;
  justify-content: space-around;
  margin-top: 0.5rem;
  color: var(--text-light);
  font-size: 0.9rem;
}

.achievements-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1.5rem;
}

.achievement-badge {
  text-align: center;
  padding: 1.5rem;
  background: var(--light-bg);
  border-radius: 12px;
}

.achievement-badge.locked {
  opacity: 0.6;
}

.badge-icon {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.8rem;
  margin: 0 auto 1rem;
}

.achievement-badge h4 {
  color: var(--text-dark);
  margin-bottom: 0.3rem;
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
  padding: 1.5rem;
  background: var(--light-bg);
  border-radius: 12px;
}

.course-thumbnail {
  width: 150px;
  height: 100px;
  border-radius: 10px;
  flex-shrink: 0;
  position: relative;
  overflow: hidden;
}

.course-thumbnail svg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.course-details {
  flex: 1;
}

.course-details h3 {
  color: var(--text-dark);
  margin-bottom: 1rem;
}

.progress-bar {
  height: 8px;
  background: #ddd;
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 0.5rem;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
  border-radius: 4px;
  transition: width 0.3s;
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
  background: var(--light-bg);
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

.form-group {
  margin-bottom: 1rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  color: var(--text-dark);
  font-size: 0.9rem;
}

.form-group input {
  width: 100%;
  padding: 0.8rem;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-size: 1rem;
}

.settings-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0.7rem 0;
  border-bottom: 1px solid var(--light-bg);
}

.settings-row:last-child {
  border-bottom: none;
}

.settings-label {
  font-size: 0.95rem;
  color: var(--text-dark);
}

.settings-value {
  font-size: 0.9rem;
  color: var(--text-light);
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

.btn {
  display: inline-block;
  padding: 0.8rem 2rem;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s;
  border: none;
  cursor: pointer;
  font-size: 1rem;
}

.btn-primary {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
}

.btn-secondary {
  background: transparent;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.btn-secondary:hover {
  background: var(--primary-color);
  color: var(--white);
}

.btn-small {
  padding: 0.5rem 1rem;
  font-size: 0.85rem;
}

@media (max-width: 768px) {
  .profile-layout {
    flex-direction: column;
  }

  .profile-sidebar {
    width: 100%;
  }

  .overview-cards {
    grid-template-columns: 1fr;
  }

  .achievements-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .learning-course-card {
    flex-direction: column;
  }

  .course-thumbnail {
    width: 100%;
    height: 120px;
  }

  .cert-grid {
    grid-template-columns: 1fr;
  }
}
</style>
