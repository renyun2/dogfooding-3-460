<template>
  <div class="home">
    <section class="banner">
      <div class="slider">
        <div 
          v-for="(slide, index) in slides" 
          :key="index" 
          class="slide" 
          :class="{ active: currentSlide === index }"
          :style="{ background: slide.background }"
        >
          <div class="slide-content">
            <div class="slide-text">
              <h2>{{ slide.title }}</h2>
              <p>{{ slide.description }}</p>
              <router-link :to="slide.link" class="btn btn-primary">{{ slide.buttonText }} →</router-link>
            </div>
            <div class="slide-illustration" v-html="slide.illustration"></div>
          </div>
        </div>
      </div>
      <div class="slider-controls">
        <button class="prev" @click="prevSlide">‹</button>
        <button class="next" @click="nextSlide">›</button>
      </div>
      <div class="slider-dots">
        <div 
          v-for="(_, index) in slides" 
          :key="index" 
          class="dot" 
          :class="{ active: currentSlide === index }"
          @click="goToSlide(index)"
        ></div>
      </div>
    </section>

    <section class="features">
      <div class="container">
        <h2 class="section-title">平台特色</h2>
        <div class="feature-grid">
          <div class="feature-card" v-for="feature in features" :key="feature.title">
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="popular-courses">
      <div class="container">
        <h2 class="section-title">热门课程推荐</h2>
        <div class="course-grid">
          <div class="course-card" v-for="course in courses" :key="course.title">
            <div class="course-image" :style="{ background: course.background }">
              <div v-html="course.illustration"></div>
            </div>
            <div class="course-info">
              <h3>{{ course.title }}</h3>
              <p class="course-desc">{{ course.description }}</p>
              <div class="course-meta">
                <span class="course-level">{{ course.level }}</span>
                <span class="course-students">{{ course.students }}人学习</span>
              </div>
              <button class="btn btn-primary">立即学习 →</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="stats">
      <div class="container">
        <div class="stats-grid">
          <div class="stat-item" v-for="stat in stats" :key="stat.label">
            <div class="stat-number" :data-target="stat.value">{{ animatedStats[stat.label] || stat.value }}</div>
            <p>{{ stat.label }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
let slideInterval = null
const animatedStats = ref({})

const slides = [
  {
    title: '🎓 开启智慧学习之旅',
    description: '个性化学习路径，助力快速成长',
    buttonText: '立即开始',
    link: '/courses',
    background: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)',
    illustration: `<svg width="320" height="260" viewBox="0 0 320 260">
      <circle cx="160" cy="130" r="120" fill="rgba(255,255,255,.1)"/>
      <rect x="50" y="185" width="220" height="12" rx="4" fill="rgba(255,255,255,.5)"/>
      <rect x="70" y="197" width="10" height="40" rx="3" fill="rgba(255,255,255,.35)"/>
      <rect x="240" y="197" width="10" height="40" rx="3" fill="rgba(255,255,255,.35)"/>
      <rect x="105" y="115" width="110" height="72" rx="6" fill="rgba(255,255,255,.25)" stroke="rgba(255,255,255,.6)" stroke-width="2"/>
      <rect x="112" y="122" width="96" height="58" rx="3" fill="rgba(20,20,60,.3)"/>
      <rect x="118" y="130" width="55" height="3" rx="1" fill="rgba(255,255,255,.7)"/>
      <rect x="118" y="138" width="40" height="3" rx="1" fill="#a0e9ff"/>
      <rect x="118" y="146" width="65" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
      <rect x="118" y="154" width="35" height="3" rx="1" fill="#ffd166"/>
      <rect x="118" y="162" width="50" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
      <path d="M98 187 L100 185 L220 185 L222 187 Z" fill="rgba(255,255,255,.5)"/>
      <rect x="60" y="158" width="30" height="28" rx="2" fill="rgba(255,255,255,.4)"/>
      <rect x="64" y="162" width="22" height="3" rx="1" fill="rgba(255,255,255,.7)"/>
      <rect x="64" y="170" width="18" height="2" rx="1" fill="rgba(255,255,255,.5)"/>
      <rect x="64" y="176" width="20" height="2" rx="1" fill="rgba(255,255,255,.5)"/>
      <rect x="240" y="162" width="28" height="24" rx="2" fill="rgba(255,255,255,.35)" transform="rotate(-8 254 174)"/>
      <line x1="240" y1="185" x2="252" y2="130" stroke="rgba(255,255,255,.5)" stroke-width="3"/>
      <ellipse cx="252" cy="128" rx="18" ry="8" fill="rgba(255,255,255,.35)"/>
      <ellipse cx="252" cy="128" rx="8" ry="4" fill="rgba(255,240,180,.6)"/>
      <circle cx="160" cy="96" r="18" fill="rgba(255,255,255,.7)"/>
      <circle cx="154" cy="93" r="2.5" fill="#667eea"/>
      <circle cx="166" cy="93" r="2.5" fill="#667eea"/>
      <path d="M155 101 Q160 106 165 101" fill="none" stroke="#667eea" stroke-width="1.5" stroke-linecap="round"/>
      <path d="M140 130 Q140 113 160 113 Q180 113 180 130 L178 185 L142 185Z" fill="rgba(255,255,255,.45)"/>
      <path d="M178 140 Q200 145 195 155" fill="none" stroke="rgba(255,255,255,.6)" stroke-width="4" stroke-linecap="round"/>
      <circle cx="56" cy="60" r="14" fill="rgba(255,255,255,.2)"/>
      <circle cx="56" cy="60" r="8" fill="rgba(255,240,100,.5)"/>
      <text x="56" y="65" text-anchor="middle" font-size="10">💡</text>
      <text x="278" y="68" font-size="14" fill="rgba(255,255,255,.6)">✦</text>
      <text x="292" y="100" font-size="10" fill="rgba(255,255,255,.4)">✦</text>
      <text x="42" y="100" font-size="10" fill="rgba(255,255,255,.4)">✦</text>
    </svg>`
  },
  {
    title: '📚 海量优质课程',
    description: '涵盖编程、设计、商业等多个领域',
    buttonText: '浏览课程',
    link: '/courses',
    background: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)',
    illustration: `<svg width="320" height="260" viewBox="0 0 320 260">
      <circle cx="160" cy="130" r="120" fill="rgba(255,255,255,.08)"/>
      <rect x="30" y="40" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
      <rect x="30" y="40" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
      <text x="88" y="70" text-anchor="middle" font-size="24">💻</text>
      <rect x="40" y="92" width="70" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
      <rect x="40" y="102" width="50" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
      <rect x="40" y="111" width="35" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
      <rect x="40" y="119" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
      <rect x="40" y="119" width="65" height="4" rx="2" fill="#ffd166"/>
      <rect x="158" y="40" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
      <rect x="158" y="40" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
      <text x="216" y="70" text-anchor="middle" font-size="24">🎨</text>
      <rect x="168" y="92" width="70" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
      <rect x="168" y="102" width="55" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
      <rect x="168" y="111" width="40" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
      <rect x="168" y="119" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
      <rect x="168" y="119" width="85" height="4" rx="2" fill="#06d6a0"/>
      <rect x="30" y="142" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
      <rect x="30" y="142" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
      <text x="88" y="172" text-anchor="middle" font-size="24">🐍</text>
      <rect x="40" y="194" width="65" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
      <rect x="40" y="204" width="45" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
      <rect x="40" y="213" width="38" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
      <rect x="40" y="221" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
      <rect x="40" y="221" width="45" height="4" rx="2" fill="#ff6b6b"/>
      <rect x="158" y="142" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
      <rect x="158" y="142" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
      <text x="216" y="172" text-anchor="middle" font-size="24">🤖</text>
      <rect x="168" y="194" width="70" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
      <rect x="168" y="204" width="55" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
      <rect x="168" y="213" width="42" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
      <rect x="168" y="221" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
      <rect x="168" y="221" width="72" height="4" rx="2" fill="#a855f7"/>
      <rect x="110" y="10" width="100" height="26" rx="13" fill="rgba(255,255,255,.3)"/>
      <text x="160" y="28" text-anchor="middle" font-size="12" font-weight="bold" fill="white">500+ 精品课程</text>
    </svg>`
  },
  {
    title: '🤖 智能学习计划',
    description: 'AI驱动，为你定制专属学习方案',
    buttonText: '制定计划',
    link: '/plan',
    background: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)',
    illustration: `<svg width="320" height="260" viewBox="0 0 320 260">
      <circle cx="160" cy="130" r="120" fill="rgba(255,255,255,.08)"/>
      <circle cx="160" cy="120" r="46" fill="rgba(255,255,255,.18)" stroke="rgba(255,255,255,.5)" stroke-width="2"/>
      <circle cx="160" cy="120" r="32" fill="rgba(255,255,255,.25)"/>
      <text x="160" y="113" text-anchor="middle" font-size="16" font-weight="bold" fill="white">AI</text>
      <text x="160" y="133" text-anchor="middle" font-size="9" fill="rgba(255,255,255,.85)">智能分析</text>
      <line x1="160" y1="74" x2="160" y2="50" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <line x1="192" y1="88" x2="210" y2="72" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <line x1="206" y1="120" x2="232" y2="120" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <line x1="192" y1="152" x2="210" y2="170" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <line x1="160" y1="166" x2="160" y2="192" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <line x1="128" y1="152" x2="110" y2="170" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <line x1="114" y1="120" x2="88" y2="120" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <line x1="128" y1="88" x2="110" y2="72" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
      <circle cx="160" cy="44" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="160" y="49" text-anchor="middle" font-size="12">📝</text>
      <circle cx="216" cy="66" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="216" y="71" text-anchor="middle" font-size="12">💻</text>
      <circle cx="240" cy="120" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="240" y="125" text-anchor="middle" font-size="12">⚡</text>
      <circle cx="216" cy="175" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="216" y="180" text-anchor="middle" font-size="12">🎯</text>
      <circle cx="160" cy="198" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="160" y="203" text-anchor="middle" font-size="12">🏆</text>
      <circle cx="104" cy="175" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="104" y="180" text-anchor="middle" font-size="12">🎨</text>
      <circle cx="80" cy="120" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="80" y="125" text-anchor="middle" font-size="12">🔬</text>
      <circle cx="104" cy="66" r="14" fill="rgba(255,255,255,.3)"/>
      <text x="104" y="71" text-anchor="middle" font-size="12">📊</text>
      <text x="28" y="50" font-size="16" fill="rgba(255,255,255,.5)">✦</text>
      <text x="282" y="50" font-size="12" fill="rgba(255,255,255,.4)">✦</text>
      <text x="288" y="195" font-size="16" fill="rgba(255,255,255,.4)">✦</text>
    </svg>`
  }
]

const features = [
  { icon: '📚', title: '丰富课程', description: '涵盖前端、后端、设计、人工智能等热门技术领域，满足不同学习需求' },
  { icon: '🎯', title: '智能规划', description: '根据个人基础和目标，AI智能推荐学习路径，高效提升技能' },
  { icon: '💡', title: '实战项目', description: '理论结合实践，通过真实项目案例，快速掌握实用技能' },
  { icon: '👥', title: '社区交流', description: '加入学习社区，与志同道合的伙伴一起学习成长' }
]

const courses = [
  {
    title: 'Web前端开发全栈课程',
    description: '从HTML/CSS基础到Vue/React框架，系统化学习前端开发全流程。',
    level: '入门到进阶',
    students: '8,523',
    background: 'linear-gradient(135deg, #667eea, #764ba2)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 280 160" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <rect x="30" y="18" width="220" height="130" rx="10" fill="rgba(255,255,255,.18)"/>
      <rect x="30" y="18" width="220" height="28" rx="10" fill="rgba(255,255,255,.3)"/>
      <circle cx="50" cy="32" r="5" fill="#ff6b6b"/>
      <circle cx="64" cy="32" r="5" fill="#ffd166"/>
      <circle cx="78" cy="32" r="5" fill="#06d6a0"/>
      <rect x="92" y="26" width="140" height="12" rx="6" fill="rgba(255,255,255,.3)"/>
      <text x="100" y="35" font-size="7" fill="rgba(255,255,255,.8)">https://smartlearn.com</text>
      <rect x="42" y="54" width="38" height="80" rx="2" fill="rgba(0,0,50,.2)"/>
      <rect x="45" y="59" width="25" height="3" rx="1" fill="#a0e9ff"/>
      <rect x="45" y="66" width="18" height="3" rx="1" fill="#ffd166"/>
      <rect x="45" y="73" width="30" height="3" rx="1" fill="#a0e9ff"/>
      <rect x="45" y="80" width="20" height="3" rx="1" fill="#ff9a9e"/>
      <rect x="45" y="87" width="28" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
      <rect x="45" y="94" width="15" height="3" rx="1" fill="#ffd166"/>
      <rect x="88" y="54" width="148" height="80" rx="4" fill="rgba(255,255,255,.12)"/>
      <rect x="94" y="60" width="136" height="20" rx="3" fill="rgba(255,255,255,.25)"/>
      <rect x="94" y="86" width="60" height="42" rx="3" fill="rgba(255,255,255,.15)"/>
      <rect x="160" y="86" width="70" height="42" rx="3" fill="rgba(255,255,255,.15)"/>
      <text x="97" y="74" font-size="8" font-weight="bold" fill="white">WEB 前端开发</text>
      <circle cx="248" cy="26" r="10" fill="rgba(255,255,255,.15)"/>
    </svg>`
  },
  {
    title: 'JavaScript高级编程',
    description: '深入学习JavaScript，掌握ES6+新特性、异步编程、面向对象等高级概念。',
    level: '中级进阶',
    students: '6,234',
    background: 'linear-gradient(135deg, #f093fb, #f5576c)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 280 160" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <rect x="20" y="15" width="80" height="80" rx="6" fill="rgba(255,220,0,.35)"/>
      <text x="38" y="68" font-size="32" font-family="monospace" font-weight="bold" fill="rgba(255,255,255,.9)">JS</text>
      <rect x="112" y="20" width="96" height="86" rx="6" fill="rgba(0,0,20,.25)"/>
      <text x="120" y="38" font-size="9" font-family="monospace" fill="#ffd166">function</text>
      <text x="168" y="38" font-size="9" font-family="monospace" fill="rgba(255,255,255,.8)">sum</text>
      <text x="195" y="38" font-size="9" font-family="monospace" fill="rgba(255,255,255,.6)">()</text>
      <text x="120" y="52" font-size="9" font-family="monospace" fill="rgba(255,255,255,.5)">{</text>
      <text x="130" y="64" font-size="9" font-family="monospace" fill="#a0e9ff">return</text>
      <text x="170" y="64" font-size="9" font-family="monospace" fill="rgba(255,255,255,.7)">a+b</text>
      <text x="120" y="76" font-size="9" font-family="monospace" fill="rgba(255,255,255,.5)">}</text>
      <text x="120" y="96" font-size="9" font-family="monospace" fill="#06d6a0">// ES6+</text>
      <text x="20" y="115" font-size="8" fill="rgba(255,255,255,.7)">ES2024 · Promise · async/await</text>
    </svg>`
  },
  {
    title: 'Vue3全家桶实战开发',
    description: '全面学习Vue3框架，包括组合式API、Vue Router、Pinia状态管理等。',
    level: '中级进阶',
    students: '5,678',
    background: 'linear-gradient(135deg, #4facfe, #00f2fe)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 280 160" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <polygon points="110,12 140,62 80,62" fill="rgba(255,255,255,.35)"/>
      <polygon points="110,25 132,62 88,62" fill="rgba(255,255,255,.2)"/>
      <polygon points="110,38 124,62 96,62" fill="rgba(255,255,255,.5)"/>
      <text x="110" y="82" text-anchor="middle" font-size="13" font-weight="bold" fill="white">Vue 3</text>
      <rect x="20" y="95" width="44" height="24" rx="4" fill="rgba(255,255,255,.2)"/>
      <text x="42" y="111" text-anchor="middle" font-size="8" fill="white">App</text>
      <line x1="42" y1="119" x2="42" y2="128" stroke="rgba(255,255,255,.4)" stroke-width="1"/>
      <line x1="42" y1="128" x2="95" y2="128" stroke="rgba(255,255,255,.4)" stroke-width="1"/>
      <line x1="95" y1="128" x2="95" y2="119" stroke="rgba(255,255,255,.4)" stroke-width="1"/>
      <rect x="70" y="95" width="50" height="24" rx="4" fill="rgba(255,255,255,.2)"/>
      <text x="95" y="111" text-anchor="middle" font-size="8" fill="white">Router</text>
      <rect x="130" y="95" width="44" height="24" rx="4" fill="rgba(255,255,255,.2)"/>
      <text x="152" y="111" text-anchor="middle" font-size="8" fill="white">Pinia</text>
      <rect x="158" y="12" width="52" height="18" rx="9" fill="rgba(255,255,255,.25)"/>
      <text x="184" y="25" text-anchor="middle" font-size="8" fill="white">组合式 API</text>
    </svg>`
  }
]

const stats = [
  { value: 50000, label: '注册用户' },
  { value: 500, label: '精品课程' },
  { value: 98, label: '好评率%' },
  { value: 200, label: '讲师团队' }
]

const goToSlide = (n) => {
  if (n >= slides.length) {
    currentSlide.value = 0
  } else if (n < 0) {
    currentSlide.value = slides.length - 1
  } else {
    currentSlide.value = n
  }
}

const prevSlide = () => goToSlide(currentSlide.value - 1)
const nextSlide = () => goToSlide(currentSlide.value + 1)

const startSlideShow = () => {
  slideInterval = setInterval(() => {
    nextSlide()
  }, 5000)
}

const stopSlideShow = () => {
  clearInterval(slideInterval)
}

const animateStats = () => {
  stats.forEach(stat => {
    const target = stat.value
    const duration = 2000
    const increment = target / (duration / 16)
    let current = 0
    
    const timer = setInterval(() => {
      current += increment
      if (current >= target) {
        animatedStats.value[stat.label] = target.toLocaleString()
        clearInterval(timer)
      } else {
        animatedStats.value[stat.label] = Math.floor(current).toLocaleString()
      }
    }, 16)
  })
}

onMounted(() => {
  startSlideShow()
  
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        animateStats()
        observer.disconnect()
      }
    })
  })
  
  const statsSection = document.querySelector('.stats')
  if (statsSection) {
    observer.observe(statsSection)
  }
})

onUnmounted(() => {
  stopSlideShow()
})
</script>

<style scoped>
.banner {
  position: relative;
  height: 500px;
  overflow: hidden;
}

.slider {
  position: relative;
  height: 100%;
}

.slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 0.5s ease-in-out;
  display: flex;
  align-items: center;
  justify-content: center;
}

.slide.active {
  opacity: 1;
}

.slide-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 3rem;
  color: var(--white);
  padding: 2rem 4rem;
  width: 100%;
  max-width: 1100px;
  box-sizing: border-box;
}

.slide-text {
  flex: 1;
  text-align: left;
  animation: slideDown 0.8s ease-out;
}

.slide-illustration {
  flex: 0 0 auto;
  animation: slideUp 0.8s ease-out;
}

.slide-content h2 {
  font-size: 2.8rem;
  margin-bottom: 1rem;
  line-height: 1.25;
}

.slide-content p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  opacity: .9;
}

.slider-controls {
  position: absolute;
  top: 50%;
  width: 100%;
  display: flex;
  justify-content: space-between;
  padding: 0 2rem;
  transform: translateY(-50%);
}

.slider-controls button {
  background: rgba(255, 255, 255, 0.3);
  border: none;
  color: var(--white);
  font-size: 2rem;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
  transition: background 0.3s;
}

.slider-controls button:hover {
  background: rgba(255, 255, 255, 0.5);
}

.slider-dots {
  position: absolute;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 10px;
}

.slider-dots .dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.5);
  cursor: pointer;
  transition: background 0.3s;
}

.slider-dots .dot.active {
  background: var(--white);
}

.features {
  padding: 5rem 0;
  background: var(--bg-light);
}

.feature-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.feature-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.feature-card h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: var(--text-dark);
}

.feature-card p {
  color: var(--text-light);
  line-height: 1.8;
}

.popular-courses {
  padding: 5rem 0;
}

.course-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.course-card {
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.course-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}

.course-image {
  height: 200px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--white);
  font-size: 1.5rem;
  font-weight: bold;
  position: relative;
}

.course-info {
  padding: 1.5rem;
}

.course-info h3 {
  font-size: 1.3rem;
  margin-bottom: 0.8rem;
  color: var(--text-dark);
}

.course-desc {
  color: var(--text-light);
  margin-bottom: 1rem;
  line-height: 1.6;
}

.course-meta {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
  font-size: 0.9rem;
}

.course-level {
  background: var(--bg-light);
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  color: var(--primary-color);
  font-weight: 500;
}

.course-students {
  color: var(--text-light);
}

.stats {
  padding: 5rem 0;
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
}

.stat-item {
  text-align: center;
}

.stat-number {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.stat-item p {
  font-size: 1.1rem;
  opacity: 0.9;
}

@media (max-width: 768px) {
  .slide-content {
    flex-direction: column;
    padding: 1rem;
    text-align: center;
  }
  
  .slide-text {
    text-align: center;
  }
  
  .slide-content h2 {
    font-size: 1.8rem;
  }
  
  .slide-illustration {
    display: none;
  }
  
  .banner {
    height: 400px;
  }
}
</style>
