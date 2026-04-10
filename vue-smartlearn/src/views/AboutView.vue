<script setup lang="ts">
const teamMembers = [
  {
    name: '张伟',
    role: '创始人 & CEO',
    bio: '前阿里巴巴技术总监，15年互联网从业经验，专注在线教育领域创新。',
    bg: 'linear-gradient(135deg,#667eea,#764ba2)',
    svgType: 'zhang'
  },
  {
    name: '李娜',
    role: '首席技术官',
    bio: '前腾讯高级架构师，人工智能专家，致力于智能学习系统研发。',
    bg: 'linear-gradient(135deg,#f093fb,#f5576c)',
    svgType: 'li'
  },
  {
    name: '王强',
    role: '教学总监',
    bio: '资深教育专家，10年教学经验，主导课程体系设计与师资培训。',
    bg: 'linear-gradient(135deg,#4facfe,#00f2fe)',
    svgType: 'wang'
  },
  {
    name: '陈静',
    role: '产品总监',
    bio: '前字节跳动产品经理，擅长用户体验设计，打造极致学习体验。',
    bg: 'linear-gradient(135deg,#fa709a,#fee140)',
    svgType: 'chen'
  },
]

const missions = [
  { icon: '🎯', title: '使命', desc: '让每个人都能通过高质量的在线教育，实现个人成长和职业发展目标。' },
  { icon: '👁️', title: '愿景', desc: '成为全球领先的智能化在线学习平台，重新定义学习方式。' },
  { icon: '💎', title: '价值观', desc: '以学习者为中心，坚持创新、专业、诚信、共赢的核心价值观。' },
]

const advantages = [
  { number: '01', title: 'AI智能学习系统', desc: '运用人工智能技术，根据学习者的基础、目标和学习习惯，智能推荐最优学习路径，提供个性化的学习建议和反馈。' },
  { number: '02', title: '顶尖师资团队', desc: '汇聚来自知名科技公司的资深工程师和设计师，拥有丰富的实战经验和教学能力，确保课程内容的专业性和实用性。' },
  { number: '03', title: '项目驱动教学', desc: '采用项目制学习方式，每个课程都包含真实的企业级项目案例，让学习者在实践中掌握技能，积累项目经验。' },
  { number: '04', title: '全方位学习支持', desc: '提供在线答疑、学习社区、作业点评、就业指导等全方位服务，确保学习者能够顺利完成学习并实现职业目标。' },
]

const timeline = [
  { year: '2020', title: '平台成立', desc: '智慧学习平台正式上线，推出首批编程课程，获得天使轮融资。' },
  { year: '2021', title: '快速成长', desc: '用户突破10万，课程覆盖前端、后端、设计等多个领域，获A轮融资。' },
  { year: '2023', title: '智能升级', desc: '推出AI学习助手，实现个性化学习路径推荐，用户突破50万。' },
  { year: '2026', title: '持续创新', desc: '成为行业领先的智能学习平台，累计服务超过100万学习者。' },
]

const partners = ['腾讯教育', '阿里云', '字节跳动', '华为云', '百度智学', '京东科技']
</script>

<template>
  <div class="about-page">
    <!-- 页面标题 -->
    <section class="page-header">
      <div class="container">
        <h1>关于我们</h1>
        <p>打造最优质的在线学习体验</p>
      </div>
    </section>

    <!-- 平台简介 -->
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
            <!-- SVG 平台介绍插画 -->
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

    <!-- 我们的使命 -->
    <section class="mission-section">
      <div class="container">
        <h2 class="section-title">我们的使命</h2>
        <div class="mission-grid">
          <div v-for="item in missions" :key="item.title" class="mission-card">
            <div class="mission-icon">{{ item.icon }}</div>
            <h3>{{ item.title }}</h3>
            <p>{{ item.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 我们的优势 -->
    <section class="advantages-section">
      <div class="container">
        <h2 class="section-title">我们的优势</h2>
        <div class="advantages-list">
          <div v-for="adv in advantages" :key="adv.number" class="advantage-item">
            <div class="advantage-number">{{ adv.number }}</div>
            <div class="advantage-content">
              <h3>{{ adv.title }}</h3>
              <p>{{ adv.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 团队介绍 -->
    <section class="team-section">
      <div class="container">
        <h2 class="section-title">核心团队</h2>
        <div class="team-grid">
          <div v-for="member in teamMembers" :key="member.name" class="team-member">
            <div class="member-avatar" :style="{ background: member.bg }">
              <!-- 张伟 CEO -->
              <svg v-if="member.svgType === 'zhang'" width="100" height="100" viewBox="0 0 100 100">
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
              </svg>
              <!-- 李娜 CTO -->
              <svg v-else-if="member.svgType === 'li'" width="100" height="100" viewBox="0 0 100 100">
                <path d="M18 100 Q18 68 50 68 Q82 68 82 100Z" fill="rgba(80,20,60,.8)"/>
                <circle cx="50" cy="69" r="3" fill="rgba(255,200,220,.6)"/>
                <circle cx="50" cy="46" r="22" fill="#f5c5a3"/>
                <path d="M28 36 Q26 20 50 18 Q74 20 72 36 L74 50 Q78 65 72 68 Q72 55 68 46" fill="#4a2c0a"/>
                <path d="M28 36 Q24 55 28 68 Q32 55 32 46" fill="#4a2c0a"/>
                <path d="M72 55 Q80 60 76 70" fill="none" stroke="#4a2c0a" stroke-width="4" stroke-linecap="round"/>
                <path d="M28 55 Q20 60 24 70" fill="none" stroke="#4a2c0a" stroke-width="4" stroke-linecap="round"/>
                <rect x="33" y="37" width="13" height="9" rx="3" fill="none" stroke="#6a3c7a" stroke-width="1.8"/>
                <rect x="54" y="37" width="13" height="9" rx="3" fill="none" stroke="#6a3c7a" stroke-width="1.8"/>
                <line x1="46" y1="42" x2="54" y2="42" stroke="#6a3c7a" stroke-width="1.5"/>
                <line x1="30" y1="41" x2="33" y2="41" stroke="#6a3c7a" stroke-width="1.5"/>
                <line x1="67" y1="41" x2="70" y2="41" stroke="#6a3c7a" stroke-width="1.5"/>
                <path d="M34 37 Q39 35 45 37" fill="none" stroke="#4a2c0a" stroke-width="1.8" stroke-linecap="round"/>
                <path d="M55 37 Q61 35 66 37" fill="none" stroke="#4a2c0a" stroke-width="1.8" stroke-linecap="round"/>
                <circle cx="39.5" cy="42" r="2" fill="#4a2c0a"/>
                <circle cx="60.5" cy="42" r="2" fill="#4a2c0a"/>
                <circle cx="40.2" cy="40.3" r=".7" fill="white"/>
                <circle cx="61.2" cy="40.3" r=".7" fill="white"/>
                <path d="M48 46 Q50 50 52 46" fill="none" stroke="#c8956a" stroke-width="1.2" stroke-linecap="round"/>
                <path d="M42 54 Q50 60 58 54" fill="none" stroke="#c8956a" stroke-width="1.8" stroke-linecap="round"/>
                <ellipse cx="28" cy="46" rx="3" ry="4.5" fill="#f5c5a3"/>
                <ellipse cx="72" cy="46" rx="3" ry="4.5" fill="#f5c5a3"/>
                <circle cx="28" cy="50" r="2" fill="rgba(255,150,180,.8)"/>
                <circle cx="72" cy="50" r="2" fill="rgba(255,150,180,.8)"/>
              </svg>
              <!-- 王强 教学总监 -->
              <svg v-else-if="member.svgType === 'wang'" width="100" height="100" viewBox="0 0 100 100">
                <path d="M18 100 Q18 68 50 68 Q82 68 82 100Z" fill="rgba(20,70,120,.8)"/>
                <polygon points="50,68 43,78 50,74 57,78" fill="white" opacity=".85"/>
                <circle cx="50" cy="46" r="22" fill="#f0b88a"/>
                <path d="M28 36 Q30 18 50 18 Q70 18 72 36 L70 28 Q62 12 50 12 Q38 12 30 28Z" fill="#2c1a0a"/>
                <rect x="33" y="38" width="13" height="9" rx="2.5" fill="none" stroke="#1a3a5e" stroke-width="1.8"/>
                <rect x="54" y="38" width="13" height="9" rx="2.5" fill="none" stroke="#1a3a5e" stroke-width="1.8"/>
                <line x1="46" y1="42" x2="54" y2="42" stroke="#1a3a5e" stroke-width="1.5"/>
                <line x1="30" y1="41" x2="33" y2="41" stroke="#1a3a5e" stroke-width="1.5"/>
                <line x1="67" y1="41" x2="70" y2="41" stroke="#1a3a5e" stroke-width="1.5"/>
                <path d="M34 37 Q39 35 45 37" fill="none" stroke="#2c1a0a" stroke-width="1.8" stroke-linecap="round"/>
                <path d="M55 37 Q61 35 66 37" fill="none" stroke="#2c1a0a" stroke-width="1.8" stroke-linecap="round"/>
                <circle cx="39.5" cy="42" r="2" fill="#2c1a0a"/>
                <circle cx="60.5" cy="42" r="2" fill="#2c1a0a"/>
                <circle cx="40.2" cy="41.2" r=".7" fill="white"/>
                <circle cx="61.2" cy="41.2" r=".7" fill="white"/>
                <path d="M48 47 Q50 51 52 47" fill="none" stroke="#b07040" stroke-width="1.2" stroke-linecap="round"/>
                <path d="M41 54 Q50 60 59 54" fill="none" stroke="#b07040" stroke-width="1.8" stroke-linecap="round"/>
                <ellipse cx="28" cy="46" rx="3" ry="4.5" fill="#f0b88a"/>
                <ellipse cx="72" cy="46" rx="3" ry="4.5" fill="#f0b88a"/>
              </svg>
              <!-- 陈静 产品总监 -->
              <svg v-else-if="member.svgType === 'chen'" width="100" height="100" viewBox="0 0 100 100">
                <path d="M18 100 Q18 68 50 68 Q82 68 82 100Z" fill="rgba(180,60,20,.7)"/>
                <circle cx="50" cy="46" r="22" fill="#f5c5a3"/>
                <path d="M28 36 Q28 18 50 16 Q72 18 72 36 L70 28 Q62 10 50 10 Q38 10 30 28Z" fill="#1a0a00"/>
                <path d="M70 22 Q85 18 84 30 Q82 42 72 40" fill="#1a0a00"/>
                <path d="M28 55 Q20 60 24 70" fill="none" stroke="#1a0a00" stroke-width="4" stroke-linecap="round"/>
                <path d="M67 22 Q75 18 76 28" fill="none" stroke="#ff6b6b" stroke-width="3" stroke-linecap="round"/>
                <path d="M35 37 Q40 34 45 37" fill="none" stroke="#1a0a00" stroke-width="1.6" stroke-linecap="round"/>
                <path d="M55 37 Q60 34 65 37" fill="none" stroke="#1a0a00" stroke-width="1.6" stroke-linecap="round"/>
                <path d="M35 41 Q40 37 45 41 Q40 45 35 41Z" fill="white"/>
                <circle cx="40" cy="41" r="2.2" fill="#1a0a00"/>
                <circle cx="40.8" cy="40.2" r=".7" fill="white"/>
                <path d="M55 41 Q60 37 65 41 Q60 45 55 41Z" fill="white"/>
                <circle cx="60" cy="41" r="2.2" fill="#1a0a00"/>
                <circle cx="60.8" cy="40.2" r=".7" fill="white"/>
                <ellipse cx="36" cy="51" rx="5" ry="3" fill="rgba(255,120,120,.25)"/>
                <ellipse cx="64" cy="51" rx="5" ry="3" fill="rgba(255,120,120,.25)"/>
                <path d="M48 47 Q50 51 52 47" fill="none" stroke="#c8956a" stroke-width="1.2" stroke-linecap="round"/>
                <path d="M40 54 Q50 62 60 54" fill="none" stroke="#c8956a" stroke-width="2" stroke-linecap="round"/>
                <ellipse cx="28" cy="46" rx="3" ry="4.5" fill="#f5c5a3"/>
                <ellipse cx="72" cy="46" rx="3" ry="4.5" fill="#f5c5a3"/>
                <circle cx="28" cy="50" r="2.5" fill="none" stroke="#ffd166" stroke-width="1.5"/>
                <circle cx="72" cy="50" r="2.5" fill="none" stroke="#ffd166" stroke-width="1.5"/>
              </svg>
            </div>
            <h3>{{ member.name }}</h3>
            <p class="member-title">{{ member.role }}</p>
            <p class="member-bio">{{ member.bio }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 发展历程 -->
    <section class="timeline-section">
      <div class="container">
        <h2 class="section-title">发展历程</h2>
        <div class="timeline">
          <div v-for="item in timeline" :key="item.year" class="timeline-item">
            <div class="timeline-year">{{ item.year }}</div>
            <div class="timeline-content">
              <h3>{{ item.title }}</h3>
              <p>{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 合作伙伴 -->
    <section class="partners-section">
      <div class="container">
        <h2 class="section-title">合作伙伴</h2>
        <div class="partners-grid">
          <div v-for="partner in partners" :key="partner" class="partner-logo">{{ partner }}</div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.page-header {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
  padding: 4rem 0;
  text-align: center;
}

.page-header h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.page-header p {
  font-size: 1.3rem;
  opacity: 0.9;
}

.about-intro {
  padding: 5rem 0;
  background: var(--white);
}

.intro-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.intro-text h2 {
  font-size: 2.2rem;
  color: var(--text-dark);
  margin-bottom: 1.5rem;
}

.intro-text .lead {
  font-size: 1.2rem;
  color: var(--primary-color);
  font-weight: 500;
  margin-bottom: 1.5rem;
  line-height: 1.8;
}

.intro-text p {
  color: var(--text-light);
  line-height: 1.8;
  margin-bottom: 1rem;
}

.intro-image {
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
}

.mission-section {
  padding: 5rem 0;
  background: var(--light-bg);
}

.section-title {
  text-align: center;
  font-size: 2.2rem;
  margin-bottom: 3rem;
  color: var(--primary-color);
}

.mission-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.mission-card {
  background: var(--white);
  padding: 2.5rem;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.mission-card:hover {
  transform: translateY(-5px);
}

.mission-icon {
  font-size: 3.5rem;
  margin-bottom: 1rem;
}

.mission-card h3 {
  color: var(--text-dark);
  margin-bottom: 1rem;
  font-size: 1.3rem;
}

.mission-card p {
  color: var(--text-light);
  line-height: 1.7;
}

.advantages-section {
  padding: 5rem 0;
  background: var(--white);
}

.advantages-list {
  display: flex;
  flex-direction: column;
  gap: 2rem;
  max-width: 900px;
  margin: 0 auto;
}

.advantage-item {
  display: flex;
  gap: 2rem;
  align-items: flex-start;
  padding: 2rem;
  background: var(--light-bg);
  border-radius: 15px;
  transition: transform 0.3s;
}

.advantage-item:hover {
  transform: translateX(10px);
}

.advantage-number {
  font-size: 2.5rem;
  font-weight: bold;
  color: var(--primary-color);
  opacity: 0.3;
  line-height: 1;
}

.advantage-content h3 {
  color: var(--text-dark);
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
}

.advantage-content p {
  color: var(--text-light);
  line-height: 1.7;
}

.team-section {
  padding: 5rem 0;
  background: var(--light-bg);
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.team-member {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.team-member:hover {
  transform: translateY(-5px);
}

.member-avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin: 0 auto 1.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.team-member h3 {
  color: var(--text-dark);
  margin-bottom: 0.3rem;
}

.member-title {
  color: var(--primary-color);
  font-size: 0.95rem;
  margin-bottom: 1rem;
}

.member-bio {
  color: var(--text-light);
  font-size: 0.9rem;
  line-height: 1.6;
}

.timeline-section {
  padding: 5rem 0;
  background: var(--white);
}

.timeline {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background: linear-gradient(to bottom, var(--primary-color), var(--secondary-color));
}

.timeline-item {
  display: flex;
  justify-content: flex-end;
  padding-right: 50%;
  position: relative;
  margin-bottom: 3rem;
}

.timeline-item:nth-child(even) {
  justify-content: flex-start;
  padding-right: 0;
  padding-left: 50%;
}

.timeline-year {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--white);
  font-weight: bold;
  font-size: 0.9rem;
}

.timeline-content {
  background: var(--light-bg);
  padding: 1.5rem;
  border-radius: 10px;
  max-width: 300px;
}

.timeline-content h3 {
  color: var(--text-dark);
  margin-bottom: 0.5rem;
}

.timeline-content p {
  color: var(--text-light);
  font-size: 0.9rem;
  line-height: 1.6;
}

.partners-section {
  padding: 5rem 0;
  background: var(--light-bg);
}

.partners-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 2rem;
}

.partner-logo {
  background: var(--white);
  padding: 2rem;
  border-radius: 10px;
  text-align: center;
  font-weight: 600;
  color: var(--text-light);
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
  transition: all 0.3s;
}

.partner-logo:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
  color: var(--primary-color);
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 2rem;
  }

  .intro-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .advantage-item {
    flex-direction: column;
    text-align: center;
  }

  .timeline::before {
    left: 20px;
  }

  .timeline-item,
  .timeline-item:nth-child(even) {
    padding-left: 60px;
    padding-right: 0;
    justify-content: flex-start;
  }

  .timeline-year {
    left: 20px;
    transform: translateX(-50%);
  }

  .partners-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
