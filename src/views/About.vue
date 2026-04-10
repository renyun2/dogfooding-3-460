<template>
  <div class="about-page">
    <section class="page-header">
      <div class="container">
        <h1>关于我们</h1>
        <p>打造最优质的在线学习体验</p>
      </div>
    </section>

    <section class="about-intro">
      <div class="container">
        <div class="intro-content">
          <div class="intro-text">
            <h2>智慧学习平台</h2>
            <p class="lead">智慧学习平台成立于2020年，是一家专注于在线教育的科技公司。我们致力于通过先进的技术和优质的内容，为每一位学习者提供个性化、高效率的学习体验。</p>
            <p>我们相信，学习是改变人生的最强大力量。通过智能化的学习路径规划、丰富的课程资源和专业的师资团队，我们帮助数万名学习者实现了职业转型和技能提升的目标。</p>
            <p>无论你是想要转行进入科技行业的零基础学习者，还是希望进一步提升专业技能的在职人员，智慧学习平台都能为你提供最适合的学习方案。</p>
          </div>
          <div class="intro-image">
            <svg width="100%" viewBox="0 0 460 400" style="border-radius:10px;display:block" xmlns="http://www.w3.org/2000/svg">
              <defs>
                <linearGradient id="bgGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                  <stop offset="0%" style="stop-color:#667eea"/>
                  <stop offset="100%" style="stop-color:#764ba2"/>
                </linearGradient>
                <linearGradient id="screenGrad" x1="0%" y1="0%" x2="0%" y2="100%">
                  <stop offset="0%" style="stop-color:#1a1a3e"/>
                  <stop offset="100%" style="stop-color:#2a2a5e"/>
                </linearGradient>
              </defs>
              <rect width="460" height="400" fill="url(#bgGrad)" rx="10"/>
              <circle cx="410" cy="40" r="55" fill="rgba(255,255,255,.06)"/>
              <circle cx="50" cy="360" r="70" fill="rgba(255,255,255,.05)"/>
              <rect x="60" y="40" width="340" height="220" rx="12" fill="rgba(255,255,255,.18)" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
              <rect x="60" y="40" width="340" height="28" rx="12" fill="rgba(255,255,255,.28)"/>
              <circle cx="82" cy="54" r="5" fill="#ff6b6b"/>
              <circle cx="96" cy="54" r="5" fill="#ffd166"/>
              <circle cx="110" cy="54" r="5" fill="#06d6a0"/>
              <rect x="130" y="48" width="160" height="12" rx="6" fill="rgba(255,255,255,.25)"/>
              <text x="210" y="58" text-anchor="middle" font-size="8" fill="rgba(255,255,255,.8)">smartlearn.com</text>
              <rect x="68" y="68" width="324" height="184" fill="url(#screenGrad)"/>
              <rect x="68" y="68" width="60" height="184" fill="rgba(255,255,255,.06)"/>
              <rect x="75" y="82" width="44" height="8" rx="4" fill="rgba(255,255,255,.4)"/>
              <rect x="75" y="96" width="36" height="6" rx="3" fill="rgba(255,255,255,.25)"/>
              <rect x="75" y="108" width="40" height="6" rx="3" fill="rgba(255,255,255,.25)"/>
              <rect x="75" y="120" width="32" height="6" rx="3" fill="rgba(255,255,255,.25)"/>
              <rect x="75" y="132" width="38" height="6" rx="3" fill="rgba(255,255,255,.25)"/>
              <rect x="75" y="144" width="34" height="6" rx="3" fill="rgba(255,255,255,.25)"/>
              <rect x="140" y="80" width="160" height="12" rx="4" fill="rgba(255,255,255,.5)"/>
              <text x="148" y="90" font-size="9" fill="rgba(255,255,255,.9)">我的学习仪表板</text>
              <rect x="140" y="100" width="75" height="45" rx="6" fill="rgba(255,255,255,.1)"/>
              <text x="178" y="116" text-anchor="middle" font-size="8" fill="rgba(255,255,255,.6)">本周学习</text>
              <text x="178" y="132" text-anchor="middle" font-size="14" font-weight="bold" fill="white">8.5h</text>
              <text x="178" y="143" text-anchor="middle" font-size="7" fill="#06d6a0">↑20%</text>
              <rect x="224" y="100" width="75" height="45" rx="6" fill="rgba(255,255,255,.1)"/>
              <text x="262" y="116" text-anchor="middle" font-size="8" fill="rgba(255,255,255,.6)">完成任务</text>
              <text x="262" y="132" text-anchor="middle" font-size="14" font-weight="bold" fill="white">24</text>
              <text x="262" y="143" text-anchor="middle" font-size="7" fill="#ffd166">本月75%</text>
              <rect x="308" y="100" width="75" height="45" rx="6" fill="rgba(255,255,255,.1)"/>
              <text x="346" y="116" text-anchor="middle" font-size="8" fill="rgba(255,255,255,.6)">学习积分</text>
              <text x="346" y="132" text-anchor="middle" font-size="14" font-weight="bold" fill="white">2350</text>
              <text x="346" y="143" text-anchor="middle" font-size="7" fill="#a0e9ff">前15%</text>
              <text x="140" y="162" font-size="8" fill="rgba(255,255,255,.7)">课程进度</text>
              <rect x="140" y="167" width="240" height="6" rx="3" fill="rgba(255,255,255,.15)"/>
              <rect x="140" y="167" width="156" height="6" rx="3" fill="#06d6a0"/>
              <text x="384" y="173" font-size="7" fill="rgba(255,255,255,.6)">65%</text>
              <rect x="140" y="178" width="240" height="6" rx="3" fill="rgba(255,255,255,.15)"/>
              <rect x="140" y="178" width="96" height="6" rx="3" fill="#ffd166"/>
              <text x="384" y="184" font-size="7" fill="rgba(255,255,255,.6)">40%</text>
              <rect x="140" y="189" width="240" height="6" rx="3" fill="rgba(255,255,255,.15)"/>
              <rect x="140" y="189" width="192" height="6" rx="3" fill="#a0e9ff"/>
              <text x="384" y="195" font-size="7" fill="rgba(255,255,255,.6)">80%</text>
              <rect x="140" y="204" width="58" height="42" rx="5" fill="rgba(255,255,255,.1)"/>
              <rect x="140" y="204" width="58" height="22" rx="5" fill="rgba(102,126,234,.4)"/>
              <text x="169" y="219" text-anchor="middle" font-size="12">💻</text>
              <rect x="144" y="228" width="50" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
              <rect x="207" y="204" width="58" height="42" rx="5" fill="rgba(255,255,255,.1)"/>
              <rect x="207" y="204" width="58" height="22" rx="5" fill="rgba(245,87,108,.4)"/>
              <text x="236" y="219" text-anchor="middle" font-size="12">🎨</text>
              <rect x="211" y="228" width="50" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
              <rect x="274" y="204" width="58" height="42" rx="5" fill="rgba(255,255,255,.1)"/>
              <rect x="274" y="204" width="58" height="22" rx="5" fill="rgba(79,172,254,.4)"/>
              <text x="303" y="219" text-anchor="middle" font-size="12">🐍</text>
              <rect x="278" y="228" width="50" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
              <rect x="195" y="260" width="70" height="10" rx="3" fill="rgba(255,255,255,.3)"/>
              <rect x="215" y="270" width="30" height="18" rx="2" fill="rgba(255,255,255,.25)"/>
              <rect x="185" y="288" width="90" height="8" rx="4" fill="rgba(255,255,255,.2)"/>
              <g transform="translate(30, 155) rotate(-12)">
                <rect width="76" height="52" rx="6" fill="rgba(255,215,0,.25)" stroke="rgba(255,215,0,.5)" stroke-width="1.5"/>
                <text x="38" y="20" text-anchor="middle" font-size="8" fill="rgba(255,255,255,.8)">结业证书</text>
                <rect x="10" y="26" width="56" height="3" rx="1" fill="rgba(255,255,255,.4)"/>
                <rect x="18" y="34" width="40" height="3" rx="1" fill="rgba(255,255,255,.3)"/>
                <text x="38" y="48" text-anchor="middle" font-size="10">🏅</text>
              </g>
              <g transform="translate(345, 268)">
                <rect width="100" height="46" rx="8" fill="rgba(6,214,160,.25)" stroke="rgba(6,214,160,.5)" stroke-width="1.5"/>
                <text x="50" y="16" text-anchor="middle" font-size="8" fill="white">课程更新提醒</text>
                <text x="50" y="28" text-anchor="middle" font-size="8" fill="rgba(255,255,255,.7)">Vue 3 新章节已上线</text>
                <text x="50" y="40" text-anchor="middle" font-size="8" fill="#06d6a0">立即学习 →</text>
              </g>
              <g transform="translate(30, 290)">
                <rect width="90" height="34" rx="8" fill="rgba(160,80,220,.3)" stroke="rgba(160,80,220,.5)" stroke-width="1.5"/>
                <text x="45" y="14" text-anchor="middle" font-size="8" fill="rgba(255,255,255,.8)">🤖 AI 学习助手</text>
                <text x="45" y="28" text-anchor="middle" font-size="7" fill="rgba(255,255,255,.6)">为你推荐3门课程</text>
              </g>
              <text x="145" y="360" font-size="11" font-weight="bold" fill="rgba(255,255,255,.9)">50,000+</text>
              <text x="145" y="375" font-size="9" fill="rgba(255,255,255,.6)">注册用户</text>
              <text x="235" y="360" font-size="11" font-weight="bold" fill="rgba(255,255,255,.9)">500+</text>
              <text x="235" y="375" font-size="9" fill="rgba(255,255,255,.6)">精品课程</text>
              <text x="305" y="360" font-size="11" font-weight="bold" fill="rgba(255,255,255,.9)">98%</text>
              <text x="305" y="375" font-size="9" fill="rgba(255,255,255,.6)">好评率</text>
              <text x="370" y="360" font-size="11" font-weight="bold" fill="rgba(255,255,255,.9)">200+</text>
              <text x="370" y="375" font-size="9" fill="rgba(255,255,255,.6)">讲师团队</text>
            </svg>
          </div>
        </div>
      </div>
    </section>

    <section class="mission-section">
      <div class="container">
        <h2 class="section-title">我们的使命</h2>
        <div class="mission-grid">
          <div class="mission-card" v-for="item in missions" :key="item.title">
            <div class="mission-icon">{{ item.icon }}</div>
            <h3>{{ item.title }}</h3>
            <p>{{ item.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="advantages-section">
      <div class="container">
        <h2 class="section-title">我们的优势</h2>
        <div class="advantages-list">
          <div class="advantage-item" v-for="(item, index) in advantages" :key="item.title">
            <div class="advantage-number">{{ String(index + 1).padStart(2, '0') }}</div>
            <div class="advantage-content">
              <h3>{{ item.title }}</h3>
              <p>{{ item.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="team-section">
      <div class="container">
        <h2 class="section-title">核心团队</h2>
        <div class="team-grid">
          <div class="team-member" v-for="member in team" :key="member.name">
            <div class="member-avatar" :style="{ background: member.background }">
              <div v-html="member.avatar"></div>
            </div>
            <h3>{{ member.name }}</h3>
            <p class="member-title">{{ member.title }}</p>
            <p class="member-bio">{{ member.bio }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const missions = [
  { icon: '🎯', title: '使命', description: '让每个人都能通过高质量的在线教育，实现个人成长和职业发展目标。' },
  { icon: '👁️', title: '愿景', description: '成为全球领先的智能化在线学习平台，重新定义学习方式。' },
  { icon: '💎', title: '价值观', description: '以学习者为中心，坚持创新、专业、诚信、共赢的核心价值观。' }
]

const advantages = [
  { title: 'AI智能学习系统', description: '运用人工智能技术，根据学习者的基础、目标和学习习惯，智能推荐最优学习路径，提供个性化的学习建议和反馈。' },
  { title: '顶尖师资团队', description: '汇聚来自知名科技公司的资深工程师和设计师，拥有丰富的实战经验和教学能力，确保课程内容的专业性和实用性。' },
  { title: '项目驱动教学', description: '采用项目制学习方式，每个课程都包含真实的企业级项目案例，让学习者在实践中掌握技能，积累项目经验。' },
  { title: '全方位学习支持', description: '提供在线答疑、学习社区、作业点评、就业指导等全方位服务，确保学习者能够顺利完成学习并实现职业目标。' }
]

const team = [
  { 
    name: '张伟', 
    title: '创始人 & CEO', 
    bio: '前阿里巴巴技术总监，15年互联网从业经验，专注在线教育领域创新。', 
    background: 'linear-gradient(135deg,#667eea,#764ba2)', 
    avatar: `<svg width="100" height="100" viewBox="0 0 100 100">
      <path d="M18 100 Q18 68 50 68 Q82 68 82 100Z" fill="rgba(30,40,90,.85)"/>
      <polygon points="50,68 42,80 50,76 58,80" fill="white" opacity=".9"/>
      <polygon points="50,76 47,86 50,84 53,86" fill="#ffd166"/>
      <circle cx="50" cy="46" r="22" fill="#f5c5a3"/>
      <path d="M28 40 Q28 20 50 20 Q72 20 72 40 L72 34 Q65 15 50 15 Q35 15 28 34Z" fill="#3d2b1a"/>
      <path d="M36 37 Q42 34 44 37" fill="none" stroke="#3d2b1a" stroke-width="1.8" stroke-linecap="round"/>
      <path d="M56 37 Q58 34 64 37" fill="none" stroke="#3d2b1a" stroke-width="1.8" stroke-linecap="round"/>
      <ellipse cx="40" cy="41" rx="3.5" ry="3" fill="white"/>
      <circle cx="40" cy="41" r="2" fill="#3d2b1a"/>
      <circle cx="40.8" cy="40.2" r=".7" fill="white"/>
      <ellipse cx="60" cy="41" rx="3.5" ry="3" fill="white"/>
      <circle cx="60" cy="41" r="2" fill="#3d2b1a"/>
      <circle cx="60.8" cy="40.2" r=".7" fill="white"/>
      <path d="M48 46 Q50 50 52 46" fill="none" stroke="#c8956a" stroke-width="1.2" stroke-linecap="round"/>
      <path d="M40 54 Q50 61 60 54" fill="none" stroke="#c8956a" stroke-width="1.8" stroke-linecap="round"/>
      <ellipse cx="28" cy="46" rx="3" ry="4.5" fill="#f5c5a3"/>
      <ellipse cx="72" cy="46" rx="3" ry="4.5" fill="#f5c5a3"/>
    </svg>` 
  },
  { 
    name: '李娜', 
    title: '联合创始人 & CTO', 
    bio: '前字节跳动架构师，10年技术经验，专注于教育科技产品研发。', 
    background: 'linear-gradient(135deg,#f093fb,#f5576c)', 
    avatar: `<svg width="100" height="100" viewBox="0 0 100 100">
      <path d="M18 100 Q18 68 50 68 Q82 68 82 100Z" fill="rgba(80,20,60,.8)"/>
      <circle cx="50" cy="69" r="3" fill="rgba(255,200,220,.6)"/>
      <circle cx="50" cy="46" r="22" fill="#f5c5a3"/>
      <path d="M28 38 Q26 20 50 18 Q74 20 72 38 L74 50 Q78 65 72 68 Q72 55 68 46" fill="#4a2c0a"/>
      <path d="M28 38 Q24 55 28 68 Q32 55 32 46" fill="#4a2c0a"/>
      <path d="M72 55 Q80 60 76 70" fill="none" stroke="#4a2c0a" stroke-width="4" stroke-linecap="round"/>
      <path d="M28 55 Q20 60 24 70" fill="none" stroke="#4a2c0a" stroke-width="4" stroke-linecap="round"/>
      <rect x="33" y="37" width="13" height="9" rx="3" fill="none" stroke="#6a3c7a" stroke-width="1.8"/>
      <rect x="54" y="37" width="13" height="9" rx="3" fill="none" stroke="#6a3c7a" stroke-width="1.8"/>
      <line x1="46" y1="41" x2="54" y2="41" stroke="#6a3c7a" stroke-width="1.5"/>
      <ellipse cx="40" cy="41" rx="3" ry="2.5" fill="#4a2c0a"/>
      <ellipse cx="60" cy="41" rx="3" ry="2.5" fill="#4a2c0a"/>
      <path d="M40 54 Q50 60 60 54" fill="none" stroke="#c8956a" stroke-width="1.5" stroke-linecap="round"/>
    </svg>` 
  },
  { 
    name: '王强', 
    title: '产品总监', 
    bio: '前腾讯产品经理，深耕在线教育领域，擅长用户体验设计。', 
    background: 'linear-gradient(135deg,#4facfe,#00f2fe)', 
    avatar: `<svg width="100" height="100" viewBox="0 0 100 100">
      <path d="M18 100 Q18 68 50 68 Q82 68 82 100Z" fill="rgba(30,60,100,.85)"/>
      <polygon points="50,68 42,80 50,76 58,80" fill="white" opacity=".9"/>
      <circle cx="50" cy="46" r="22" fill="#f5c5a3"/>
      <path d="M28 42 Q28 22 50 22 Q72 22 72 42 L72 36 Q65 18 50 18 Q35 18 28 36Z" fill="#2a1810"/>
      <ellipse cx="40" cy="41" rx="3.5" ry="3" fill="white"/>
      <circle cx="40" cy="41" r="2" fill="#2a1810"/>
      <ellipse cx="60" cy="41" rx="3.5" ry="3" fill="white"/>
      <circle cx="60" cy="41" r="2" fill="#2a1810"/>
      <path d="M40 54 Q50 60 60 54" fill="none" stroke="#c8956a" stroke-width="1.8" stroke-linecap="round"/>
    </svg>` 
  },
  { 
    name: '陈静', 
    title: '教研总监', 
    bio: '资深教育专家，曾任职于知名高校，专注课程体系设计与教学研究。', 
    background: 'linear-gradient(135deg,#fa709a,#fee140)', 
    avatar: `<svg width="100" height="100" viewBox="0 0 100 100">
      <path d="M18 100 Q18 68 50 68 Q82 68 82 100Z" fill="rgba(180,60,100,.8)"/>
      <circle cx="50" cy="69" r="3" fill="rgba(255,200,220,.6)"/>
      <circle cx="50" cy="46" r="22" fill="#f5c5a3"/>
      <path d="M28 38 Q26 18 50 16 Q74 18 72 38 L74 48 Q78 62 72 66 Q72 52 68 44" fill="#3d2817"/>
      <path d="M28 38 Q24 52 28 66 Q32 52 32 44" fill="#3d2817"/>
      <ellipse cx="40" cy="41" rx="3.5" ry="3" fill="white"/>
      <circle cx="40" cy="41" r="2" fill="#3d2817"/>
      <ellipse cx="60" cy="41" rx="3.5" ry="3" fill="white"/>
      <circle cx="60" cy="41" r="2" fill="#3d2817"/>
      <path d="M40 54 Q50 60 60 54" fill="none" stroke="#c8956a" stroke-width="1.5" stroke-linecap="round"/>
    </svg>` 
  }
]
</script>

<style scoped>
.about-intro {
  padding: 4rem 0;
}

.intro-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
}

.intro-text h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  color: var(--text-dark);
}

.intro-text .lead {
  font-size: 1.1rem;
  color: var(--text-dark);
  margin-bottom: 1rem;
}

.intro-text p {
  color: var(--text-light);
  line-height: 1.8;
  margin-bottom: 1rem;
}

.mission-section {
  padding: 5rem 0;
  background: var(--bg-light);
}

.mission-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.mission-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.mission-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.mission-card h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: var(--text-dark);
}

.mission-card p {
  color: var(--text-light);
  line-height: 1.8;
}

.advantages-section {
  padding: 5rem 0;
}

.advantages-list {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.advantage-item {
  display: flex;
  gap: 2rem;
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.advantage-item:hover {
  transform: translateX(10px);
}

.advantage-number {
  font-size: 3rem;
  font-weight: bold;
  color: var(--primary-color);
  opacity: 0.3;
}

.advantage-content h3 {
  font-size: 1.3rem;
  margin-bottom: 0.8rem;
  color: var(--text-dark);
}

.advantage-content p {
  color: var(--text-light);
  line-height: 1.8;
}

.team-section {
  padding: 5rem 0;
  background: var(--bg-light);
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.team-member {
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.team-member:hover {
  transform: translateY(-5px);
}

.member-avatar {
  height: 150px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.team-member h3 {
  margin: 1rem 0 0.5rem;
  color: var(--text-dark);
}

.member-title {
  color: var(--primary-color);
  font-weight: 500;
  margin-bottom: 0.5rem;
}

.member-bio {
  padding: 0 1.5rem 1.5rem;
  color: var(--text-light);
  font-size: 0.9rem;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .intro-content {
    grid-template-columns: 1fr;
  }
  
  .intro-image {
    order: -1;
  }
  
  .advantage-item {
    flex-direction: column;
    gap: 1rem;
  }
}
</style>
