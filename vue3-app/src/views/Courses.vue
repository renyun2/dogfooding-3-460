<template>
  <div class="courses">
    <div class="page-header">
      <div class="container">
        <h1>课程中心</h1>
        <p>海量优质课程，助你快速成长</p>
      </div>
    </div>
    
    <section class="course-filter">
      <div class="container">
        <div class="filter-tabs">
          <button 
            v-for="tab in filterTabs" 
            :key="tab.id"
            class="filter-btn" 
            :class="{ active: activeCategory === tab.id }"
            @click="filterCourses(tab.id)"
          >
            {{ tab.name }}
          </button>
        </div>
        <div class="filter-search">
          <input 
            type="text" 
            id="searchInput" 
            placeholder="搜索课程..." 
            v-model="searchTerm"
            @keyup.enter="performSearch"
          >
          <button id="searchBtn" @click="performSearch">搜索</button>
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
            :data-category="course.category"
            @click="handleCourseClick(course.title)"
          >
            <div 
              class="course-thumbnail"
              :style="{ background: course.gradient }"
            >
              <span class="course-badge" v-if="course.hot">🔥 热门</span>
            </div>
            <div class="course-details">
              <h3>{{ course.title }}</h3>
              <div class="course-instructor">讲师：{{ course.instructor }}</div>
              <div class="course-description">{{ course.description }}</div>
              <div class="course-stats">
                <span>⏱️ {{ course.duration }}</span>
                <span>📚 {{ course.lessons }}个课时</span>
                <span>⭐ {{ course.rating }}分</span>
              </div>
              <div class="course-price">¥{{ course.price }}</div>
              <router-link to="/courses" class="btn btn-primary btn-small">立即学习</router-link>
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

const filterTabs = [
  { id: 'all', name: '全部课程' },
  { id: 'frontend', name: '前端开发' },
  { id: 'backend', name: '后端开发' },
  { id: 'design', name: 'UI/UX设计' },
  { id: 'data', name: '数据分析' },
  { id: 'ai', name: '人工智能' }
]

const allCourses = [
  {
    title: 'Vue3 + Vite 企业级开发实战',
    category: 'frontend',
    instructor: '张老师',
    description: '深入学习Vue3核心API、组合式API、Vite构建工具，掌握企业级项目开发流程。',
    duration: '40小时',
    lessons: 120,
    rating: 4.9,
    price: 299,
    hot: true,
    gradient: 'linear-gradient(135deg,#667eea,#764ba2)'
  },
  {
    title: 'React全家桶开发指南',
    category: 'frontend',
    instructor: '李老师',
    description: '系统学习React、Redux、React Router等技术栈，打造高质量前端应用。',
    duration: '45小时',
    lessons: 135,
    rating: 4.8,
    price: 329,
    hot: false,
    gradient: 'linear-gradient(135deg,#667eea,#764ba2)'
  },
  {
    title: 'Node.js后端开发实战',
    category: 'backend',
    instructor: '王老师',
    description: '从Node.js基础到Express框架，掌握后端API开发和数据库设计。',
    duration: '35小时',
    lessons: 100,
    rating: 4.7,
    price: 269,
    hot: true,
    gradient: 'linear-gradient(135deg,#f093fb,#f5576c)'
  },
  {
    title: 'Figma UI/UX设计进阶',
    category: 'design',
    instructor: '陈老师',
    description: '掌握Figma高级技巧、设计系统、交互原型设计，成为专业设计师。',
    duration: '30小时',
    lessons: 80,
    rating: 4.9,
    price: 249,
    hot: false,
    gradient: 'linear-gradient(135deg,#4facfe,#00f2fe)'
  },
  {
    title: 'Python数据分析入门到精通',
    category: 'data',
    instructor: '刘老师',
    description: '学习Pandas、NumPy、Matplotlib，掌握数据分析核心技能。',
    duration: '50小时',
    lessons: 150,
    rating: 4.8,
    price: 359,
    hot: true,
    gradient: 'linear-gradient(135deg,#f093fb,#f5576c)'
  },
  {
    title: '深度学习与神经网络',
    category: 'ai',
    instructor: '赵老师',
    description: '从零开始学习神经网络、CNN、RNN等深度学习核心技术。',
    duration: '60小时',
    lessons: 180,
    rating: 4.7,
    price: 459,
    hot: false,
    gradient: 'linear-gradient(135deg,#a855f7,#6366f1)'
  }
]

const filteredCourses = computed(() => {
  let result = allCourses
  
  if (activeCategory.value !== 'all') {
    result = result.filter(course => course.category === activeCategory.value)
  }
  
  if (searchTerm.value.trim()) {
    const term = searchTerm.value.toLowerCase().trim()
    result = result.filter(course => 
      course.title.toLowerCase().includes(term) ||
      course.description.toLowerCase().includes(term)
    )
  }
  
  return result
})

const filterCourses = (category) => {
  activeCategory.value = category
}

const performSearch = () => {
  // 搜索逻辑已通过computed实现
}

const handleCourseClick = (title) => {
  const toastEvent = new CustomEvent('showToast', {
    detail: { 
      message: `📖 正在进入《${title}》...`, 
      type: 'success',
      duration: 3000
    }
  })
  window.dispatchEvent(toastEvent)
}
</script>
