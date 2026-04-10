<template>
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
              <li><a :class="{active: activeTab === 'overview'}" @click.prevent="activeTab = 'overview'">📊 学习概览</a></li>
              <li><a :class="{active: activeTab === 'courses'}" @click.prevent="activeTab = 'courses'">📚 我的课程</a></li>
              <li><a :class="{active: activeTab === 'progress'}" @click.prevent="activeTab = 'progress'">📈 学习进度</a></li>
              <li><a :class="{active: activeTab === 'certificates'}" @click.prevent="activeTab = 'certificates'">🏅 我的证书</a></li>
              <li><a :class="{active: activeTab === 'settings'}" @click.prevent="activeTab = 'settings'">⚙️ 账户设置</a></li>
            </ul>
          </nav>
        </aside>

        <!-- 主内容区 -->
        <main class="profile-content">

          <div class="profile-panel" :class="{active: activeTab === 'overview'}">
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

          <div class="profile-panel" :class="{active: activeTab === 'courses'}">
            <div class="content-section">
              <h2>我的课程</h2>
              <div class="learning-courses">

                <div class="learning-course-card">
                  <div class="course-thumbnail" style="position:relative; background:linear-gradient(135deg,#667eea,#764ba2)">
                    <svg width="150" height="100" viewBox="0 0 150 100" style="position:absolute;top:0;left:0;width:100%;height:100%">
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
                  </div>
                  <div class="course-details">
                    <h3>Web前端开发全栈课程</h3>
                    <div class="progress-bar">
                      <div class="progress-fill" style="width:65%"></div>
                    </div>
                    <div class="progress-info">
                      <span>已完成 65%</span>
                      <span>剩余 15 课时</span>
                    </div>
                    <button class="btn btn-primary" @click="continueLearn">继续学习 →</button>
                  </div>
                </div>

                <div class="learning-course-card">
                  <div class="course-thumbnail" style="position:relative; background:linear-gradient(135deg,#f093fb,#f5576c)">
                    <svg width="150" height="100" viewBox="0 0 150 100" style="position:absolute;top:0;left:0;width:100%;height:100%">
                      <text x="32" y="68" font-size="52" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.3)">{</text>
                      <text x="98" y="68" font-size="52" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.3)">}</text>
                      <text x="58" y="58" font-size="22" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.9)">JS</text>
                      <rect x="50" y="65" width="50" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
                      <rect x="55" y="73" width="40" height="3" rx="1" fill="rgba(255,255,255,.35)"/>
                    </svg>
                  </div>
                  <div class="course-details">
                    <h3>JavaScript高级编程</h3>
                    <div class="progress-bar">
                      <div class="progress-fill" style="width:40%"></div>
                    </div>
                    <div class="progress-info">
                      <span>已完成 40%</span>
                      <span>剩余 27 课时</span>
                    </div>
                    <button class="btn btn-primary" @click="continueLearn">继续学习 →</button>
                  </div>
                </div>

                <div class="learning-course-card">
                  <div class="course-thumbnail" style="position:relative; background:linear-gradient(135deg,#4facfe,#00f2fe)">
                    <svg width="150" height="100" viewBox="0 0 150 100" style="position:absolute;top:0;left:0;width:100%;height:100%">
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
                    <h3>UI/UX设计实战</h3>
                    <div class="progress-bar">
                      <div class="progress-fill" style="width:80%"></div>
                    </div>
                    <div class="progress-info">
                      <span>已完成 80%</span>
                      <span>剩余 7 课时</span>
                    </div>
                    <button class="btn btn-primary" @click="continueLearn">继续学习 →</button>
                  </div>
                </div>

              </div>
            </div>
          </div>

          <div class="profile-panel" :class="{active: activeTab === 'progress'}">
            <div class="content-section">
              <h2>学习进度</h2>
              <div class="progress-detail-list">
                <div class="progress-detail-item">
                  <div class="pd-header">
                    <h4>💻 Web前端开发全栈课程</h4>
                    <span class="pd-pct">65%</span>
                  </div>
                  <div class="pd-bar"><div class="pd-fill" style="width:65%"></div></div>
                  <p class="pd-meta">已学 28课时 · 剩余 15课时 · 预计 3周完成</p>
                </div>
                <div class="progress-detail-item">
                  <div class="pd-header">
                    <h4>⚡ JavaScript高级编程</h4>
                    <span class="pd-pct">40%</span>
                  </div>
                  <div class="pd-bar"><div class="pd-fill" style="width:40%"></div></div>
                  <p class="pd-meta">已学 18课时 · 剩余 27课时 · 预计 5周完成</p>
                </div>
                <div class="progress-detail-item">
                  <div class="pd-header">
                    <h4>🎨 UI/UX设计实战</h4>
                    <span class="pd-pct">80%</span>
                  </div>
                  <div class="pd-bar"><div class="pd-fill" style="width:80%"></div></div>
                  <p class="pd-meta">已学 28课时 · 剩余 7课时 · 预计 1周完成</p>
                </div>
                <div class="progress-detail-item">
                  <div class="pd-header">
                    <h4>🐍 Python数据分析</h4>
                    <span class="pd-pct">15%</span>
                  </div>
                  <div class="pd-bar"><div class="pd-fill" style="width:15%"></div></div>
                  <p class="pd-meta">已学 6课时 · 剩余 36课时 · 预计 8周完成</p>
                </div>
                <div class="progress-detail-item">
                  <div class="pd-header">
                    <h4>🤖 机器学习入门</h4>
                    <span class="pd-pct">5%</span>
                  </div>
                  <div class="pd-bar"><div class="pd-fill" style="width:5%"></div></div>
                  <p class="pd-meta">已学 3课时 · 剩余 52课时 · 预计 12周完成</p>
                </div>
              </div>
            </div>
          </div>

          <div class="profile-panel" :class="{active: activeTab === 'certificates'}">
            <div class="content-section">
              <h2>我的证书</h2>
              <div class="cert-grid">

                <div class="cert-card">
                  <div class="cert-banner" style="background:linear-gradient(135deg,#667eea,#764ba2)">
                    <svg width="200" height="140" viewBox="0 0 200 140">
                      <rect x="20" y="15" width="160" height="110" rx="8" fill="rgba(255,255,255,.15)" stroke="rgba(255,255,255,.4)" stroke-width="1.5"/>
                      <text x="100" y="48" text-anchor="middle" font-size="13" font-weight="bold" fill="white">智慧学习平台</text>
                      <text x="100" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.8)">结业证书</text>
                      <text x="100" y="82" text-anchor="middle" font-size="11" font-weight="bold" fill="white">HTML5+CSS3网页开发基础</text>
                      <circle cx="100" cy="110" r="12" fill="#ffd700"/>
                      <text x="100" y="115" text-anchor="middle" font-size="12" fill="#764ba2">★</text>
                    </svg>
                  </div>
                  <div class="cert-body">
                    <h4>HTML5+CSS3 网页开发基础</h4>
                    <p>全面掌握现代网页开发基础技能</p>
                    <span class="cert-date">📅 颁发日期：2025-11-10</span>
                  </div>
                </div>

                <div class="cert-card">
                  <div class="cert-banner" style="background:linear-gradient(135deg,#4facfe,#00f2fe)">
                    <svg width="200" height="140" viewBox="0 0 200 140">
                      <rect x="20" y="15" width="160" height="110" rx="8" fill="rgba(255,255,255,.15)" stroke="rgba(255,255,255,.4)" stroke-width="1.5"/>
                      <text x="100" y="48" text-anchor="middle" font-size="13" font-weight="bold" fill="white">智慧学习平台</text>
                      <text x="100" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.8)">结业证书</text>
                      <text x="100" y="82" text-anchor="middle" font-size="11" font-weight="bold" fill="white">UI/UX 设计基础</text>
                      <circle cx="100" cy="110" r="12" fill="#ffd700"/>
                      <text x="100" y="115" text-anchor="middle" font-size="12" fill="#0077b6">★</text>
                    </svg>
                  </div>
                  <div class="cert-body">
                    <h4>UI/UX 用户体验设计基础</h4>
                    <p>掌握用户研究与交互设计方法论</p>
                    <span class="cert-date">📅 颁发日期：2025-12-25</span>
                  </div>
                </div>

                <div class="cert-card">
                  <div class="cert-banner" style="background:linear-gradient(135deg,#fa709a,#fee140)">
                    <svg width="200" height="140" viewBox="0 0 200 140">
                      <rect x="20" y="15" width="160" height="110" rx="8" fill="rgba(255,255,255,.15)" stroke="rgba(255,255,255,.4)" stroke-width="1.5"/>
                      <text x="100" y="48" text-anchor="middle" font-size="13" font-weight="bold" fill="white">智慧学习平台</text>
                      <text x="100" y="63" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.8)">结业证书</text>
                      <text x="100" y="82" text-anchor="middle" font-size="11" font-weight="bold" fill="white">Python 编程入门</text>
                      <circle cx="100" cy="110" r="12" fill="#ffd700"/>
                      <text x="100" y="115" text-anchor="middle" font-size="12" fill="#c9184a">★</text>
                    </svg>
                  </div>
                  <div class="cert-body">
                    <h4>Python 编程入门</h4>
                    <p>掌握 Python 基础语法与编程思维</p>
                    <span class="cert-date">📅 颁发日期：2026-01-15</span>
                  </div>
                </div>

              </div>
            </div>
          </div>

          <div class="profile-panel" :class="{active: activeTab === 'settings'}">
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
                    <input type="checkbox" checked>
                    <span class="toggle-slider"></span>
                  </label>
                </div>
                <div class="settings-row">
                  <span class="settings-label">学习提醒</span>
                  <label class="toggle-switch">
                    <input type="checkbox" checked>
                    <span class="toggle-slider"></span>
                  </label>
                </div>
                <div class="settings-row">
                  <span class="settings-label">新课程推荐</span>
                  <label class="toggle-switch">
                    <input type="checkbox">
                    <span class="toggle-slider"></span>
                  </label>
                </div>
                <div class="settings-row">
                  <span class="settings-label">活动和优惠推送</span>
                  <label class="toggle-switch">
                    <input type="checkbox">
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
                    <input type="checkbox" checked>
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
</template>

<script setup>
import { ref } from 'vue'

const activeTab = ref('overview')

const continueLearn = () => {
  showToast('▶️ 恢复学习进度中...', 'info')
  setTimeout(() => {
    showToast('欢迎回来！继续你的学习 💪', 'success')
  }, 800)
}

const showToast = (message, type) => {
  const toastEvent = new CustomEvent('showToast', { 
    detail: { message, type } 
  })
  window.dispatchEvent(toastEvent)
}
</script>
