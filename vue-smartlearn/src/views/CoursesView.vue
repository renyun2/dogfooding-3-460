<script setup lang="ts">
import { ref, computed } from 'vue'

const activeCategory = ref('all')
const searchQuery = ref('')

const categories = [
  { id: 'all', name: '全部课程' },
  { id: 'frontend', name: '前端开发' },
  { id: 'backend', name: '后端开发' },
  { id: 'design', name: 'UI设计' },
  { id: 'ai', name: '人工智能' },
  { id: 'data', name: '数据分析' },
]

const courses = [
  {
    id: 1,
    title: 'HTML5+CSS3网页开发基础',
    instructor: '张老师',
    description: '从零开始学习网页开发，掌握HTML5和CSS3核心技术，打造现代化响应式网页。',
    duration: '30课时',
    students: '8,523人学习',
    price: '¥199',
    category: 'frontend',
    badge: '热门',
    bg: 'linear-gradient(135deg,#667eea,#764ba2)',
    svgType: 'html'
  },
  {
    id: 2,
    title: 'JavaScript高级编程',
    instructor: '李老师',
    description: '深入学习JavaScript，掌握ES6+新特性、异步编程、面向对象等高级概念。',
    duration: '45课时',
    students: '6,234人学习',
    price: '¥299',
    category: 'frontend',
    badge: '推荐',
    bg: 'linear-gradient(135deg,#f093fb,#f5576c)',
    svgType: 'js'
  },
  {
    id: 3,
    title: 'Vue3全家桶实战开发',
    instructor: '王老师',
    description: '全面学习Vue3框架，包括组合式API、Vue Router、Pinia状态管理等。',
    duration: '50课时',
    students: '5,678人学习',
    price: '¥399',
    category: 'frontend',
    badge: null,
    bg: 'linear-gradient(135deg,#4facfe,#00f2fe)',
    svgType: 'vue'
  },
  {
    id: 4,
    title: 'Node.js后端开发实战',
    instructor: '赵老师',
    description: '使用Node.js和Express构建RESTful API，掌握后端开发核心技能。',
    duration: '40课时',
    students: '4,892人学习',
    price: '¥349',
    category: 'backend',
    badge: null,
    bg: 'linear-gradient(135deg,#fa709a,#fee140)',
    svgType: 'node'
  },
  {
    id: 5,
    title: 'Python Web开发Django框架',
    instructor: '刘老师',
    description: '学习Django框架，快速构建功能完善的Web应用，包括ORM、模板、认证等。',
    duration: '38课时',
    students: '3,456人学习',
    price: '¥329',
    category: 'backend',
    badge: '新课',
    bg: 'linear-gradient(135deg,#30cfd0,#330867)',
    svgType: 'django'
  },
  {
    id: 6,
    title: 'Figma UI设计实战课程',
    instructor: '陈老师',
    description: '从设计基础到高级技巧，使用Figma打造专业级UI设计作品。',
    duration: '35课时',
    students: '4,123人学习',
    price: '¥279',
    category: 'design',
    badge: null,
    bg: 'linear-gradient(135deg,#a8edea,#fed6e3)',
    svgType: 'figma'
  },
  {
    id: 7,
    title: '用户体验设计UX全攻略',
    instructor: '杨老师',
    description: '学习用户研究、信息架构、交互设计等UX核心方法论。',
    duration: '32课时',
    students: '3,789人学习',
    price: '¥259',
    category: 'design',
    badge: null,
    bg: 'linear-gradient(135deg,#ffecd2,#fcb69f)',
    svgType: 'ux'
  },
  {
    id: 8,
    title: '机器学习入门到实战',
    instructor: '周老师',
    description: '系统学习机器学习算法，使用Python实现分类、回归、聚类等任务。',
    duration: '55课时',
    students: '7,234人学习',
    price: '¥499',
    category: 'ai',
    badge: '热门',
    bg: 'linear-gradient(135deg,#ff9a9e,#fecfef)',
    svgType: 'ml'
  },
  {
    id: 9,
    title: '深度学习与神经网络',
    instructor: '吴老师',
    description: '掌握深度学习框架TensorFlow/PyTorch，构建CNN、RNN等神经网络模型。',
    duration: '60课时',
    students: '5,891人学习',
    price: '¥599',
    category: 'ai',
    badge: null,
    bg: 'linear-gradient(135deg,#fbc2eb,#a6c1ee)',
    svgType: 'dl'
  },
  {
    id: 10,
    title: 'Python数据分析实战',
    instructor: '郑老师',
    description: '使用Pandas、NumPy、Matplotlib进行数据清洗、分析和可视化。',
    duration: '42课时',
    students: '6,567人学习',
    price: '¥379',
    category: 'data',
    badge: null,
    bg: 'linear-gradient(135deg,#fdcbf1,#e6dee9)',
    svgType: 'data'
  },
]

const filteredCourses = computed(() => {
  let result = courses

  if (activeCategory.value !== 'all') {
    result = result.filter(course => course.category === activeCategory.value)
  }

  if (searchQuery.value.trim()) {
    const query = searchQuery.value.toLowerCase()
    result = result.filter(course =>
      course.title.toLowerCase().includes(query) ||
      course.description.toLowerCase().includes(query)
    )
  }

  return result
})

const performSearch = () => {
  // 搜索功能已通过计算属性实现
}
</script>

<template>
  <div class="courses-page">
    <!-- 页面标题 -->
    <section class="page-header">
      <div class="container">
        <h1>课程中心</h1>
        <p>精选优质课程，助你快速成长</p>
      </div>
    </section>

    <!-- 课程筛选 -->
    <section class="course-filter">
      <div class="container">
        <div class="filter-tabs">
          <button
            v-for="cat in categories"
            :key="cat.id"
            class="filter-btn"
            :class="{ active: activeCategory === cat.id }"
            @click="activeCategory = cat.id"
          >
            {{ cat.name }}
          </button>
        </div>
        <div class="filter-search">
          <input
            type="text"
            v-model="searchQuery"
            placeholder="搜索课程..."
            @keyup.enter="performSearch"
          >
          <button @click="performSearch">🔍 搜索</button>
        </div>
      </div>
    </section>

    <!-- 课程列表 -->
    <section class="courses-section">
      <div class="container">
        <div class="courses-list">
          <div
            v-for="course in filteredCourses"
            :key="course.id"
            class="course-item"
            :class="{ 'fade-in': true }"
          >
            <div class="course-thumbnail" :style="{ background: course.bg }">
              <span v-if="course.badge" class="course-badge">{{ course.badge }}</span>
              
              <!-- HTML5 SVG -->
              <svg v-if="course.svgType === 'html'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
                <polygon points="28,10 34,82 80,96 126,82 132,10" fill="rgba(255,255,255,.2)"/>
                <polygon points="38,22 42,68 80,80 118,68 122,22" fill="rgba(255,255,255,.15)"/>
                <text x="80" y="60" text-anchor="middle" font-size="24" font-weight="bold" fill="rgba(255,255,255,.85)">5</text>
                <polygon points="145,10 151,82 185,96 219,82 225,10" fill="rgba(255,255,255,.18)" transform="translate(-30,0)"/>
                <text x="155" y="60" text-anchor="middle" font-size="14" font-weight="bold" fill="rgba(255,255,255,.8)">CSS</text>
                <text x="155" y="76" text-anchor="middle" font-size="10" fill="rgba(255,255,255,.65)">样式</text>
                <text x="10" y="115" font-size="7" font-family="monospace" fill="rgba(255,255,255,.5)">&lt;div class="hero"&gt;...&lt;/div&gt;</text>
              </svg>

              <!-- JavaScript SVG -->
              <svg v-else-if="course.svgType === 'js'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
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
              </svg>

              <!-- Vue SVG -->
              <svg v-else-if="course.svgType === 'vue'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
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
              </svg>

              <!-- Node.js SVG -->
              <svg v-else-if="course.svgType === 'node'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
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
                <path d="M110 44 L128 44" stroke="rgba(255,255,255,.5)" stroke-width="2"/>
                <text x="18" y="100" font-size="8" fill="rgba(255,255,255,.7)">REST API · Express · MongoDB</text>
              </svg>

              <!-- Django SVG -->
              <svg v-else-if="course.svgType === 'django'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
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
              </svg>

              <!-- Figma SVG -->
              <svg v-else-if="course.svgType === 'figma'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
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
              </svg>

              <!-- UX SVG -->
              <svg v-else-if="course.svgType === 'ux'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
                <circle cx="38" cy="38" r="12" fill="rgba(180,80,60,.3)"/>
                <circle cx="38" cy="32" r="6" fill="rgba(180,80,60,.5)"/>
                <path d="M25 50 Q25 40 38 40 Q51 40 51 50Z" fill="rgba(180,80,60,.5)"/>
                <path d="M54 38 Q75 20 100 38 Q125 55 148 38 Q170 22 195 38" fill="none" stroke="rgba(160,80,40,.6)" stroke-width="3" stroke-dasharray="6,3"/>
                <circle cx="75" cy="30" r="8" fill="rgba(255,140,80,.6)"/>
                <text x="75" y="34" text-anchor="middle" font-size="8" fill="white">需求</text>
                <circle cx="120" cy="50" r="8" fill="rgba(255,140,80,.6)"/>
                <text x="120" y="54" text-anchor="middle" font-size="8" fill="white">研究</text>
                <circle cx="165" cy="30" r="8" fill="rgba(255,140,80,.6)"/>
                <text x="165" y="34" text-anchor="middle" font-size="8" fill="white">设计</text>
                <circle cx="200" cy="44" r="8" fill="rgba(255,200,80,.7)"/>
                <text x="200" y="48" text-anchor="middle" font-size="8" fill="white">测试</text>
                <path d="M54 90 Q80 70 110 80 Q140 90 165 72 Q185 60 210 68" fill="none" stroke="rgba(160,80,40,.45)" stroke-width="2.5"/>
                <text x="20" y="112" font-size="8" fill="rgba(100,50,30,.7)">用户体验 · 信息架构 · 交互设计</text>
              </svg>

              <!-- ML SVG -->
              <svg v-else-if="course.svgType === 'ml'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
                <circle cx="30" cy="30" r="7" fill="rgba(200,60,80,.5)"/>
                <circle cx="30" cy="60" r="7" fill="rgba(200,60,80,.5)"/>
                <circle cx="30" cy="90" r="7" fill="rgba(200,60,80,.5)"/>
                <circle cx="82" cy="20" r="7" fill="rgba(180,60,120,.5)"/>
                <circle cx="82" cy="48" r="7" fill="rgba(180,60,120,.5)"/>
                <circle cx="82" cy="76" r="7" fill="rgba(180,60,120,.5)"/>
                <circle cx="82" cy="104" r="7" fill="rgba(180,60,120,.5)"/>
                <circle cx="138" cy="30" r="7" fill="rgba(160,80,180,.55)"/>
                <circle cx="138" cy="60" r="7" fill="rgba(160,80,180,.55)"/>
                <circle cx="138" cy="90" r="7" fill="rgba(160,80,180,.55)"/>
                <circle cx="190" cy="45" r="7" fill="rgba(120,80,200,.6)"/>
                <circle cx="190" cy="75" r="7" fill="rgba(120,80,200,.6)"/>
                <line x1="37" y1="30" x2="75" y2="20" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="37" y1="30" x2="75" y2="48" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="37" y1="60" x2="75" y2="48" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="37" y1="60" x2="75" y2="76" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="37" y1="90" x2="75" y2="76" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="37" y1="90" x2="75" y2="104" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="89" y1="20" x2="131" y2="30" stroke="rgba(255,255,255,.25)" stroke-width="1"/>
                <line x1="89" y1="48" x2="131" y2="30" stroke="rgba(255,255,255,.25)" stroke-width="1"/>
                <line x1="89" y1="48" x2="131" y2="60" stroke="rgba(255,255,255,.25)" stroke-width="1"/>
                <line x1="89" y1="76" x2="131" y2="60" stroke="rgba(255,255,255,.25)" stroke-width="1"/>
                <line x1="89" y1="76" x2="131" y2="90" stroke="rgba(255,255,255,.25)" stroke-width="1"/>
                <line x1="89" y1="104" x2="131" y2="90" stroke="rgba(255,255,255,.25)" stroke-width="1"/>
                <line x1="145" y1="30" x2="183" y2="45" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="145" y1="60" x2="183" y2="45" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="145" y1="60" x2="183" y2="75" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <line x1="145" y1="90" x2="183" y2="75" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
                <text x="10" y="120" font-size="8" fill="rgba(120,40,60,.8)">ML · 分类 · 回归 · 聚类 · Python</text>
              </svg>

              <!-- DL SVG -->
              <svg v-else-if="course.svgType === 'dl'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
                <rect x="15" y="35" width="22" height="60" rx="4" fill="rgba(180,100,200,.4)"/>
                <text x="26" y="68" text-anchor="middle" font-size="6" fill="white">输入</text>
                <text x="26" y="78" text-anchor="middle" font-size="6" fill="white">层</text>
                <rect x="50" y="25" width="22" height="80" rx="4" fill="rgba(150,80,220,.45)"/>
                <text x="61" y="63" text-anchor="middle" font-size="6" fill="white">Conv</text>
                <text x="61" y="73" text-anchor="middle" font-size="6" fill="white">Layer</text>
                <rect x="85" y="30" width="22" height="70" rx="4" fill="rgba(120,80,230,.5)"/>
                <text x="96" y="63" text-anchor="middle" font-size="6" fill="white">Pool</text>
                <text x="96" y="73" text-anchor="middle" font-size="6" fill="white">Layer</text>
                <rect x="120" y="20" width="22" height="90" rx="4" fill="rgba(100,100,240,.5)"/>
                <text x="131" y="63" text-anchor="middle" font-size="6" fill="white">FC</text>
                <text x="131" y="73" text-anchor="middle" font-size="6" fill="white">Layer</text>
                <rect x="155" y="40" width="22" height="50" rx="4" fill="rgba(80,120,230,.55)"/>
                <text x="166" y="63" text-anchor="middle" font-size="6" fill="white">输出</text>
                <text x="166" y="73" text-anchor="middle" font-size="6" fill="white">层</text>
                <line x1="37" y1="65" x2="50" y2="65" stroke="rgba(255,255,255,.5)" stroke-width="1.5"/>
                <line x1="72" y1="65" x2="85" y2="65" stroke="rgba(255,255,255,.5)" stroke-width="1.5"/>
                <line x1="107" y1="65" x2="120" y2="65" stroke="rgba(255,255,255,.5)" stroke-width="1.5"/>
                <line x1="142" y1="65" x2="155" y2="65" stroke="rgba(255,255,255,.5)" stroke-width="1.5"/>
                <rect x="188" y="30" width="26" height="16" rx="4" fill="rgba(255,165,0,.5)"/>
                <text x="201" y="42" text-anchor="middle" font-size="7" fill="white">TF</text>
                <rect x="188" y="52" width="26" height="16" rx="4" fill="rgba(255,80,80,.45)"/>
                <text x="201" y="64" text-anchor="middle" font-size="7" fill="white">PT</text>
                <text x="14" y="120" font-size="8" fill="rgba(80,50,120,.8)">CNN · RNN · Transformer · DL</text>
              </svg>

              <!-- Data SVG -->
              <svg v-else-if="course.svgType === 'data'" width="100%" height="100%" viewBox="0 0 220 130" preserveAspectRatio="xMidYMid meet" style="position:absolute;inset:0">
                <line x1="25" y1="100" x2="120" y2="100" stroke="rgba(120,60,150,.5)" stroke-width="1.5"/>
                <line x1="25" y1="30" x2="25" y2="100" stroke="rgba(120,60,150,.5)" stroke-width="1.5"/>
                <rect x="32" y="65" width="12" height="35" rx="2" fill="rgba(180,100,200,.55)"/>
                <rect x="50" y="50" width="12" height="50" rx="2" fill="rgba(160,80,220,.6)"/>
                <rect x="68" y="42" width="12" height="58" rx="2" fill="rgba(140,80,230,.65)"/>
                <rect x="86" y="58" width="12" height="42" rx="2" fill="rgba(180,100,200,.55)"/>
                <rect x="104" y="38" width="12" height="62" rx="2" fill="rgba(120,80,240,.7)"/>
                <polyline points="38,60 56,45 74,38 92,52 110,35" fill="none" stroke="rgba(255,120,150,.8)" stroke-width="2"/>
                <circle cx="38" cy="60" r="3" fill="rgba(255,120,150,.9)"/>
                <circle cx="56" cy="45" r="3" fill="rgba(255,120,150,.9)"/>
                <circle cx="74" cy="38" r="3" fill="rgba(255,120,150,.9)"/>
                <circle cx="92" cy="52" r="3" fill="rgba(255,120,150,.9)"/>
                <circle cx="110" cy="35" r="3" fill="rgba(255,120,150,.9)"/>
                <circle cx="170" cy="65" r="40" fill="rgba(255,255,255,.2)"/>
                <path d="M170,65 L170,25 A40,40 0 0,1 205,78 Z" fill="rgba(160,80,220,.6)"/>
                <path d="M170,65 L205,78 A40,40 0 0,1 148,102 Z" fill="rgba(180,100,200,.5)"/>
                <path d="M170,65 L148,102 A40,40 0 0,1 134,42 Z" fill="rgba(255,120,150,.5)"/>
                <path d="M170,65 L134,42 A40,40 0 0,1 170,25 Z" fill="rgba(120,80,240,.55)"/>
                <text x="14" y="120" font-size="8" fill="rgba(100,50,120,.8)">Pandas · NumPy · Matplotlib</text>
              </svg>
            </div>
            <div class="course-details">
              <h3>{{ course.title }}</h3>
              <p class="course-instructor">👨‍🏫 讲师：{{ course.instructor }}</p>
              <p class="course-description">{{ course.description }}</p>
              <div class="course-stats">
                <span>⏱️ {{ course.duration }}</span>
                <span>👥 {{ course.students }}</span>
                <span class="course-price">{{ course.price }}</span>
              </div>
              <button class="btn btn-primary">立即学习 →</button>
            </div>
          </div>
        </div>
        <div v-if="filteredCourses.length === 0" class="no-results">
          <p>没有找到匹配的课程</p>
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

.no-results {
  text-align: center;
  padding: 3rem;
  color: var(--text-light);
}

.fade-in {
  animation: fadeIn 0.5s ease-out;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@media (max-width: 768px) {
  .course-item {
    flex-direction: column;
  }

  .course-thumbnail {
    width: 100%;
    height: 200px;
  }

  .page-header h1 {
    font-size: 2rem;
  }
}
</style>
