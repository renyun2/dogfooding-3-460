<script setup lang="ts">
import { ref, onMounted } from 'vue'
import BannerSlider from '../components/BannerSlider.vue'

const stats = [
  { label: '注册用户', target: 50000, suffix: '' },
  { label: '精品课程', target: 500, suffix: '' },
  { label: '专业导师', target: 150, suffix: '' },
  { label: '满意度', target: 95, suffix: '%' },
]

const statValues = ref([0, 0, 0, 0])
const statsAnimated = ref(false)

const features = [
  { icon: '📚', title: '丰富课程', desc: '涵盖前端、后端、设计、人工智能等热门技术领域，满足不同学习需求' },
  { icon: '🎯', title: '智能规划', desc: '根据个人基础和目标，AI智能推荐学习路径，高效提升技能' },
  { icon: '💡', title: '实战项目', desc: '理论结合实践，通过真实项目案例，快速掌握实用技能' },
  { icon: '👥', title: '社区交流', desc: '加入学习社区，与志同道合的伙伴一起学习成长' },
]

const popularCourses = [
  {
    title: 'Web前端开发全栈课程',
    desc: '从HTML/CSS基础到Vue/React框架，全面掌握前端开发技能',
    level: '初级-高级',
    students: '12,580人学习',
    bg: 'linear-gradient(135deg,#667eea,#764ba2)',
    illustration: 'web'
  },
  {
    title: 'Python数据分析与AI',
    desc: '学习Python编程，掌握数据分析和机器学习核心技术',
    level: '中级',
    students: '9,234人学习',
    bg: 'linear-gradient(135deg,#f093fb,#f5576c)',
    illustration: 'python'
  },
  {
    title: 'UI/UX设计实战',
    desc: '从设计原则到工具实操，打造专业级用户体验设计作品',
    level: '初级-中级',
    students: '7,891人学习',
    bg: 'linear-gradient(135deg,#4facfe,#00f2fe)',
    illustration: 'design'
  },
]

const animateStats = () => {
  stats.forEach((stat, index) => {
    const duration = 2000
    const increment = stat.target / (duration / 16)
    let current = 0

    const timer = setInterval(() => {
      current += increment
      if (current >= stat.target) {
        statValues.value[index] = stat.target
        clearInterval(timer)
      } else {
        statValues.value[index] = Math.floor(current)
      }
    }, 16)
  })
}

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting && !statsAnimated.value) {
        statsAnimated.value = true
        animateStats()
      }
    })
  })

  const statsSection = document.querySelector('.stats')
  if (statsSection) {
    observer.observe(statsSection)
  }
})
</script>

<template>
  <div class="home">
    <BannerSlider />

    <!-- 特色功能 -->
    <section class="features">
      <div class="container">
        <h2 class="section-title">平台特色</h2>
        <div class="feature-grid">
          <div v-for="feature in features" :key="feature.title" class="feature-card">
            <div class="feature-icon">{{ feature.icon }}</div>
            <h3>{{ feature.title }}</h3>
            <p>{{ feature.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 热门课程 -->
    <section class="popular-courses">
      <div class="container">
        <h2 class="section-title">热门课程推荐</h2>
        <div class="course-grid">
          <div v-for="course in popularCourses" :key="course.title" class="course-card">
            <div class="course-image" :style="{ background: course.bg }">
              <!-- Web前端SVG -->
              <svg v-if="course.illustration === 'web'" width="100%" height="100%" viewBox="0 0 280 160" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
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
                <text x="248" y="30" text-anchor="middle" font-size="10">🌐</text>
              </svg>
              <!-- Python SVG -->
              <svg v-else-if="course.illustration === 'python'" width="100%" height="100%" viewBox="0 0 280 160" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
                <rect x="30" y="22" width="220" height="120" rx="8" fill="rgba(0,0,20,.35)"/>
                <rect x="30" y="22" width="220" height="22" rx="8" fill="rgba(0,0,20,.4)"/>
                <circle cx="46" cy="33" r="4" fill="#ff6b6b"/>
                <circle cx="58" cy="33" r="4" fill="#ffd166"/>
                <circle cx="70" cy="33" r="4" fill="#06d6a0"/>
                <text x="90" y="37" font-size="8" fill="rgba(255,255,255,.6)">Python Terminal</text>
                <text x="40" y="58" font-size="8" font-family="monospace" fill="#06d6a0">>>> import pandas as pd</text>
                <text x="40" y="70" font-size="8" font-family="monospace" fill="#06d6a0">>>> import numpy as np</text>
                <text x="40" y="82" font-size="8" font-family="monospace" fill="rgba(255,255,255,.7)">>>> df = pd.read_csv('data')</text>
                <text x="40" y="94" font-size="8" font-family="monospace" fill="#a0e9ff">>>> df.describe()</text>
                <rect x="180" y="55" width="58" height="75" rx="4" fill="rgba(255,255,255,.1)"/>
                <rect x="188" y="96" width="8" height="26" rx="2" fill="#ffd166" opacity=".8"/>
                <rect x="200" y="86" width="8" height="36" rx="2" fill="#a0e9ff" opacity=".8"/>
                <rect x="212" y="78" width="8" height="44" rx="2" fill="#06d6a0" opacity=".8"/>
                <rect x="224" y="90" width="8" height="32" rx="2" fill="#ff6b6b" opacity=".8"/>
                <line x1="185" y1="124" x2="235" y2="124" stroke="rgba(255,255,255,.4)" stroke-width="1"/>
                <text x="40" y="115" font-size="8" font-family="monospace" fill="#ffd166">>>> 🐍 Python 数据分析</text>
                <text x="40" y="128" font-size="8" font-family="monospace" fill="rgba(255,255,255,.4)">分析完成 ✓</text>
              </svg>
              <!-- Design SVG -->
              <svg v-else width="100%" height="100%" viewBox="0 0 280 160" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
                <rect x="28" y="20" width="145" height="125" rx="8" fill="rgba(255,255,255,.2)"/>
                <rect x="36" y="30" width="129" height="60" rx="4" fill="rgba(255,255,255,.25)"/>
                <rect x="50" y="34" width="44" height="50" rx="6" fill="rgba(0,30,80,.25)"/>
                <rect x="54" y="40" width="36" height="24" rx="2" fill="rgba(255,255,255,.3)"/>
                <rect x="54" y="68" width="20" height="4" rx="2" fill="rgba(255,255,255,.5)"/>
                <rect x="54" y="75" width="36" height="4" rx="2" fill="rgba(255,255,255,.3)"/>
                <rect x="102" y="36" width="54" height="4" rx="2" fill="rgba(255,255,255,.6)"/>
                <rect x="102" y="44" width="40" height="3" rx="2" fill="rgba(255,255,255,.4)"/>
                <rect x="102" y="51" width="50" height="3" rx="2" fill="rgba(255,255,255,.4)"/>
                <rect x="102" y="68" width="35" height="10" rx="4" fill="rgba(255,255,255,.35)"/>
                <text x="119" y="77" text-anchor="middle" font-size="7" fill="white">设计稿</text>
                <line x1="96" y1="34" x2="96" y2="84" stroke="rgba(255,255,255,.35)" stroke-width="1" stroke-dasharray="3,2"/>
                <rect x="36" y="96" width="129" height="12" rx="2" fill="rgba(255,255,255,.1)"/>
                <circle cx="48" cy="102" r="5" fill="#667eea"/>
                <circle cx="62" cy="102" r="5" fill="#f093fb"/>
                <circle cx="76" cy="102" r="5" fill="#ffd166"/>
                <circle cx="90" cy="102" r="5" fill="#06d6a0"/>
                <circle cx="104" cy="102" r="5" fill="#ff6b6b"/>
                <text x="120" y="106" font-size="7" fill="rgba(255,255,255,.7)">色彩方案</text>
                <rect x="36" y="112" width="129" height="26" rx="4" fill="rgba(255,255,255,.1)"/>
                <text x="44" y="122" font-size="7" fill="rgba(255,255,255,.8)">字体: Aa 标题 / 正文</text>
                <text x="44" y="132" font-size="7" fill="rgba(255,255,255,.6)">网格: 8px 基础栅格系统</text>
                <rect x="182" y="20" width="70" height="125" rx="8" fill="rgba(255,255,255,.15)"/>
                <text x="217" y="38" text-anchor="middle" font-size="9" font-weight="bold" fill="white">工具</text>
                <text x="217" y="58" text-anchor="middle" font-size="14">🖌️</text>
                <text x="217" y="78" text-anchor="middle" font-size="14">✏️</text>
                <text x="217" y="98" text-anchor="middle" font-size="14">🔲</text>
                <text x="217" y="118" text-anchor="middle" font-size="14">🎨</text>
                <text x="217" y="138" text-anchor="middle" font-size="14">👁️</text>
              </svg>
            </div>
            <div class="course-info">
              <h3>{{ course.title }}</h3>
              <p class="course-desc">{{ course.desc }}</p>
              <div class="course-meta">
                <span class="course-level">{{ course.level }}</span>
                <span class="course-students">👥 {{ course.students }}</span>
              </div>
              <RouterLink to="/courses" class="btn btn-secondary">查看详情 →</RouterLink>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 学习数据统计 -->
    <section class="stats">
      <div class="container">
        <div class="stats-grid">
          <div v-for="(stat, index) in stats" :key="stat.label" class="stat-item">
            <h3 class="stat-number">{{ (statValues[index] ?? 0).toLocaleString() }}{{ stat.suffix }}</h3>
            <p>{{ stat.label }}</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.features {
  padding: 5rem 0;
  background: var(--bg-light);
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 3rem;
  color: var(--text-dark);
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
  overflow: hidden;
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
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
