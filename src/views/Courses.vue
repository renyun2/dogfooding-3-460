<template>
  <div class="courses-page">
    <section class="page-header">
      <div class="container">
        <h1>课程中心</h1>
        <p>精选优质课程，助你快速成长</p>
      </div>
    </section>

    <section class="course-filter">
      <div class="container">
        <div class="filter-tabs">
          <button 
            v-for="cat in categories" 
            :key="cat.value"
            class="filter-btn" 
            :class="{ active: activeCategory === cat.value }"
            @click="filterByCategory(cat.value)"
          >
            {{ cat.label }}
          </button>
        </div>
        <div class="filter-search">
          <input 
            type="text" 
            v-model="searchTerm" 
            placeholder="搜索课程..."
            @keyup.enter="performSearch"
          >
          <button @click="performSearch">🔍 搜索</button>
        </div>
      </div>
    </section>

    <section class="courses-section">
      <div class="container">
        <div class="courses-list">
          <div 
            v-for="course in filteredCourses" 
            :key="course.title" 
            class="course-item"
            :style="{ animation: 'fadeIn 0.5s' }"
          >
            <div class="course-thumbnail" :style="{ background: course.background }">
              <span v-if="course.badge" class="course-badge">{{ course.badge }}</span>
              <div v-html="course.illustration"></div>
            </div>
            <div class="course-details">
              <h3>{{ course.title }}</h3>
              <p class="course-instructor">{{ course.instructor }}</p>
              <p class="course-description">{{ course.description }}</p>
              <div class="course-stats">
                <span>{{ course.duration }}</span>
                <span>{{ course.students }}人学习</span>
                <span class="course-price">{{ course.price }}</span>
              </div>
              <button class="btn btn-primary">立即学习 →</button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeCategory = ref('all')
const searchTerm = ref('')

const categories = [
  { value: 'all', label: '全部课程' },
  { value: 'frontend', label: '前端开发' },
  { value: 'backend', label: '后端开发' },
  { value: 'design', label: 'UI设计' },
  { value: 'ai', label: '人工智能' },
  { value: 'data', label: '数据分析' }
]

const courses = [
  {
    title: 'HTML5+CSS3网页开发基础',
    category: 'frontend',
    instructor: '👨‍🏫 讲师：张老师',
    description: '从零开始学习网页开发，掌握HTML5和CSS3核心技术，打造现代化响应式网页。',
    duration: '⏱️ 30课时',
    students: '8,523',
    price: '¥199',
    badge: '热门',
    background: 'linear-gradient(135deg,#667eea,#764ba2)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <polygon points="28,10 34,82 80,96 126,82 132,10" fill="rgba(255,255,255,.2)"/>
      <polygon points="38,22 42,68 80,80 118,68 122,22" fill="rgba(255,255,255,.15)"/>
      <text x="80" y="60" text-anchor="middle" font-size="24" font-weight="bold" fill="rgba(255,255,255,.85)">5</text>
      <polygon points="145,10 151,82 185,96 219,82 225,10" fill="rgba(255,255,255,.18)" transform="translate(-30,0)"/>
      <text x="155" y="60" text-anchor="middle" font-size="14" font-weight="bold" fill="rgba(255,255,255,.8)">CSS</text>
      <text x="155" y="76" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.65)">样式</text>
      <text x="10" y="115" font-size="7" font-family="monospace" fill="rgba(255,255,255,.5)">&lt;div class="hero"&gt;...&lt;/div&gt;</text>
    </svg>`
  },
  {
    title: 'JavaScript高级编程',
    category: 'frontend',
    instructor: '👨‍🏫 讲师：李老师',
    description: '深入学习JavaScript，掌握ES6+新特性、异步编程、面向对象等高级概念。',
    duration: '⏱️ 45课时',
    students: '6,234',
    price: '¥299',
    badge: '推荐',
    background: 'linear-gradient(135deg,#f093fb,#f5576c)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
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
    category: 'frontend',
    instructor: '👨‍🏫 讲师：王老师',
    description: '全面学习Vue3框架，包括组合式API、Vue Router、Pinia状态管理等。',
    duration: '⏱️ 50课时',
    students: '5,678',
    price: '¥399',
    badge: '',
    background: 'linear-gradient(135deg,#4facfe,#00f2fe)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <polygon points="110,12 140,62 80,62" fill="rgba(255,255,255,.35)"/>
      <polygon points="110,25 132,62 88,62" fill="rgba(255,255,255,.2)"/>
      <polygon points="110,38 124,62 96,62" fill="rgba(255,255,255,.5)"/>
      <text x="110" y="82" text-anchor="middle" font-size="13" font-weight="bold" fill="white">Vue 3</text>
      <rect x="20" y="95" width="44" height="24" rx="4" fill="rgba(255,255,255,.2)"/>
      <text x="42" y="111" text-anchor="middle" font-size="8" fill="white">App</text>
      <rect x="70" y="95" width="50" height="24" rx="4" fill="rgba(255,255,255,.2)"/>
      <text x="95" y="111" text-anchor="middle" font-size="8" fill="white">Router</text>
      <rect x="130" y="95" width="44" height="24" rx="4" fill="rgba(255,255,255,.2)"/>
      <text x="152" y="111" text-anchor="middle" font-size="8" fill="white">Pinia</text>
      <rect x="158" y="12" width="52" height="18" rx="9" fill="rgba(255,255,255,.25)"/>
      <text x="184" y="25" text-anchor="middle" font-size="8" fill="white">组合式 API</text>
    </svg>`
  },
  {
    title: 'Node.js后端开发实战',
    category: 'backend',
    instructor: '👨‍🏫 讲师：赵老师',
    description: '使用Node.js和Express构建RESTful API，掌握后端开发核心技能。',
    duration: '⏱️ 40课时',
    students: '4,892',
    price: '¥349',
    badge: '',
    background: 'linear-gradient(135deg,#fa709a,#fee140)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <polygon points="65,18 95,18 110,44 95,70 65,70 50,44" fill="rgba(255,255,255,.25)"/>
      <text x="80" y="50" text-anchor="middle" font-size="13" font-weight="bold" fill="white">Node</text>
      <text x="80" y="64" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.8)">.js</text>
      <rect x="128" y="15" width="76" height="95" rx="6" fill="rgba(255,255,255,.2)"/>
      <rect x="134" y="22" width="64" height="14" rx="3" fill="rgba(255,255,255,.3)"/>
      <circle cx="143" cy="29" r="4" fill="#06d6a0"/>
      <rect x="150" y="27" width="40" height="4" rx="2" fill="rgba(255,255,255,.5)"/>
      <rect x="134" y="42" width="64" height="14" rx="3" fill="rgba(255,255,255,.2)"/>
      <circle cx="143" cy="49" r="4" fill="#ffd166"/>
      <rect x="150" y="47" width="30" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
      <rect x="134" y="62" width="64" height="14" rx="3" fill="rgba(255,255,255,.2)"/>
      <circle cx="143" cy="69" r="4" fill="#a0e9ff"/>
      <rect x="150" y="67" width="44" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
      <text x="18" y="100" font-size="8" fill="rgba(255,255,255,.7)">REST API · Express · MongoDB</text>
    </svg>`
  },
  {
    title: 'Python Web开发Django框架',
    category: 'backend',
    instructor: '👨‍🏫 讲师：刘老师',
    description: '学习Django框架，快速构建功能完善的Web应用，包括ORM、模板、认证等。',
    duration: '⏱️ 38课时',
    students: '3,456',
    price: '¥329',
    badge: '新课',
    background: 'linear-gradient(135deg,#30cfd0,#330867)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <path d="M55,30 Q55,20 65,20 L90,20 Q100,20 100,30 L100,55 Q100,60 95,60 L75,60 Q70,60 70,65 L70,70" fill="none" stroke="rgba(160,220,255,.8)" stroke-width="8" stroke-linecap="round"/>
      <circle cx="70" cy="76" r="7" fill="rgba(160,220,255,.8)"/>
      <path d="M85,100 Q85,110 75,110 L50,110 Q40,110 40,100 L40,75 Q40,70 45,70 L65,70 Q70,70 70,65 L70,60" fill="none" stroke="rgba(255,215,0,.75)" stroke-width="8" stroke-linecap="round"/>
      <circle cx="70" cy="54" r="7" fill="rgba(255,215,0,.75)"/>
      <rect x="115" y="25" width="88" height="80" rx="6" fill="rgba(255,255,255,.15)"/>
      <text x="159" y="46" text-anchor="middle" font-size="14" font-weight="bold" fill="rgba(255,255,255,.9)">Django</text>
      <rect x="122" y="54" width="74" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
      <rect x="122" y="63" width="55" height="4" rx="2" fill="rgba(255,255,255,.3)"/>
      <rect x="122" y="72" width="65" height="4" rx="2" fill="rgba(255,255,255,.3)"/>
      <rect x="122" y="81" width="44" height="4" rx="2" fill="rgba(255,255,255,.3)"/>
      <text x="122" y="100" font-size="8" fill="rgba(255,255,255,.6)">MTV · ORM · Template</text>
    </svg>`
  },
  {
    title: 'Figma UI设计实战课程',
    category: 'design',
    instructor: '👩‍🏫 讲师：陈老师',
    description: '从设计基础到高级技巧，使用Figma打造专业级UI设计作品。',
    duration: '⏱️ 35课时',
    students: '4,123',
    price: '¥279',
    badge: '',
    background: 'linear-gradient(135deg,#a8edea,#fed6e3)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <rect x="30" y="20" width="36" height="36" rx="18" fill="rgba(255,116,101,.6)"/>
      <rect x="66" y="20" width="36" height="36" rx="18" fill="rgba(255,186,58,.6)"/>
      <rect x="30" y="56" width="36" height="36" rx="18" fill="rgba(160,220,80,.6)"/>
      <rect x="66" y="56" width="36" height="36" rx="18" fill="rgba(80,180,255,.6)"/>
      <circle cx="84" cy="74" r="18" fill="rgba(180,130,255,.6)"/>
      <text x="84" y="108" text-anchor="middle" font-size="10" font-weight="bold" fill="rgba(80,60,100,.85)">Figma</text>
      <rect x="122" y="18" width="86" height="95" rx="6" fill="rgba(255,255,255,.35)"/>
      <rect x="128" y="24" width="74" height="10" rx="3" fill="rgba(100,80,120,.25)"/>
      <rect x="128" y="40" width="34" height="28" rx="3" fill="rgba(100,80,120,.2)"/>
      <rect x="168" y="40" width="34" height="28" rx="3" fill="rgba(100,80,120,.2)"/>
      <rect x="128" y="74" width="74" height="8" rx="3" fill="rgba(100,80,120,.2)"/>
      <rect x="128" y="86" width="50" height="6" rx="3" fill="rgba(100,80,120,.15)"/>
      <rect x="128" y="96" width="62" height="12" rx="4" fill="rgba(160,130,255,.4)"/>
      <text x="159" y="106" text-anchor="middle" font-size="7" fill="rgba(80,60,100,.8)">立即设计</text>
    </svg>`
  },
  {
    title: 'AI机器学习入门到精通',
    category: 'ai',
    instructor: '👨‍🏫 讲师：孙老师',
    description: '从零开始学习机器学习，掌握Python数据分析、深度学习等核心技术。',
    duration: '⏱️ 60课时',
    students: '3,890',
    price: '¥499',
    badge: '热门',
    background: 'linear-gradient(135deg,#667eea,#764ba2)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <circle cx="110" cy="65" r="40" fill="rgba(255,255,255,.2)" stroke="rgba(255,255,255,.5)" stroke-width="2"/>
      <text x="110" y="60" text-anchor="middle" font-size="16" font-weight="bold" fill="white">AI</text>
      <text x="110" y="78" text-anchor="middle" font-size="9" fill="rgba(255,255,255,.85)">Machine Learning</text>
      <line x1="110" y1="25" x2="110" y2="15" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
      <line x1="145" y1="40" x2="155" y2="30" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
      <line x1="145" y1="90" x2="155" y2="100" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
      <line x1="75" y1="40" x2="65" y2="30" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
      <line x1="75" y1="90" x2="65" y2="100" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
      <circle cx="110" cy="10" r="6" fill="rgba(255,255,255,.3)"/>
      <circle cx="160" cy="25" r="6" fill="rgba(255,255,255,.3)"/>
      <circle cx="160" cy="105" r="6" fill="rgba(255,255,255,.3)"/>
      <circle cx="60" cy="25" r="6" fill="rgba(255,255,255,.3)"/>
      <circle cx="60" cy="105" r="6" fill="rgba(255,255,255,.3)"/>
    </svg>`
  },
  {
    title: '数据分析与可视化实战',
    category: 'data',
    instructor: '👨‍🏫 讲师：周老师',
    description: '学习Python数据分析库Pandas、NumPy，掌握数据可视化技术。',
    duration: '⏱️ 42课时',
    students: '2,567',
    price: '¥359',
    badge: '',
    background: 'linear-gradient(135deg,#11998e,#38ef7d)',
    illustration: `<svg width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
      <rect x="30" y="90" width="25" height="30" rx="3" fill="rgba(255,255,255,.5)"/>
      <rect x="65" y="60" width="25" height="60" rx="3" fill="rgba(255,255,255,.6)"/>
      <rect x="100" y="40" width="25" height="80" rx="3" fill="rgba(255,255,255,.7)"/>
      <rect x="135" y="70" width="25" height="50" rx="3" fill="rgba(255,255,255,.5)"/>
      <rect x="170" y="50" width="25" height="70" rx="3" fill="rgba(255,255,255,.6)"/>
      <line x1="25" y1="120" x2="200" y2="120" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
      <line x1="25" y1="120" x2="25" y2="30" stroke="rgba(255,255,255,.4)" stroke-width="2"/>
      <text x="110" y="25" text-anchor="middle" font-size="12" font-weight="bold" fill="white">📊 Data Analysis</text>
    </svg>`
  }
]

const filteredCourses = computed(() => {
  let result = courses
  
  if (activeCategory.value !== 'all') {
    result = result.filter(c => c.category === activeCategory.value)
  }
  
  if (searchTerm.value.trim()) {
    const term = searchTerm.value.toLowerCase()
    result = result.filter(c => 
      c.title.toLowerCase().includes(term) || 
      c.description.toLowerCase().includes(term)
    )
  }
  
  return result
})

const filterByCategory = (category) => {
  activeCategory.value = category
}

const performSearch = () => {
  // 搜索逻辑已在 computed 中处理
}
</script>

<style scoped>
.course-filter {
  padding: 2rem 0;
  background: var(--bg-light);
}

.filter-tabs {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 0.6rem 1.2rem;
  border: 2px solid var(--border-color);
  background: var(--white);
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s;
  font-weight: 500;
}

.filter-btn:hover,
.filter-btn.active {
  background: var(--primary-color);
  color: var(--white);
  border-color: var(--primary-color);
}

.filter-search {
  display: flex;
  gap: 1rem;
}

.filter-search input {
  flex: 1;
  padding: 0.8rem 1.2rem;
  border: 2px solid var(--border-color);
  border-radius: 8px;
  font-size: 1rem;
}

.filter-search button {
  padding: 0.8rem 1.5rem;
  background: var(--primary-color);
  color: var(--white);
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: 500;
  transition: background 0.3s;
}

.filter-search button:hover {
  background: var(--secondary-color);
}

.courses-section {
  padding: 3rem 0;
}

.courses-list {
  display: grid;
  gap: 2rem;
}

.course-item {
  display: flex;
  gap: 2rem;
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.course-item:hover {
  transform: translateY(-3px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
}

.course-thumbnail {
  width: 250px;
  min-height: 200px;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.course-badge {
  position: absolute;
  top: 10px;
  right: 10px;
  background: var(--warning-color);
  color: var(--white);
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: bold;
  z-index: 1;
}

.course-details {
  flex: 1;
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
}

.course-details h3 {
  font-size: 1.4rem;
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.course-instructor {
  color: var(--text-light);
  margin-bottom: 0.8rem;
}

.course-description {
  color: var(--text-light);
  line-height: 1.6;
  margin-bottom: 1rem;
  flex: 1;
}

.course-stats {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 1rem;
  color: var(--text-light);
}

.course-price {
  color: var(--error-color);
  font-weight: bold;
  font-size: 1.2rem;
}

@media (max-width: 768px) {
  .course-item {
    flex-direction: column;
  }
  
  .course-thumbnail {
    width: 100%;
    min-height: 180px;
  }
  
  .filter-search {
    flex-direction: column;
  }
}
</style>
