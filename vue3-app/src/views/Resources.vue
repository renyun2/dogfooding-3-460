<template>
  <div class="resources">
    <div class="page-header">
      <div class="container">
        <h1>学习资源</h1>
        <p>丰富的学习资源助你一臂之力</p>
      </div>
    </div>
    
    <section class="resources-section">
      <div class="container">
        <div class="resource-category">
          <h3 class="category-title">📄 文档资料</h3>
          <div class="resource-grid">
            <div v-for="resource in documents" :key="resource.title" class="resource-card">
              <div class="resource-icon">{{ resource.icon }}</div>
              <h3>{{ resource.title }}</h3>
              <p>{{ resource.description }}</p>
              <div class="resource-tags">
                <span class="tag" v-for="tag in resource.tags" :key="tag">{{ tag }}</span>
              </div>
              <a href="#" class="resource-link" @click.prevent="downloadResource(resource.title)">立即下载 →</a>
            </div>
          </div>
        </div>
        
        <div class="resource-category">
          <h3 class="category-title">📚 推荐书籍</h3>
          <div class="books-grid">
            <div v-for="book in books" :key="book.title" class="book-card">
              <div class="book-cover" :style="{ background: book.gradient }">
                <h3 class="book-title">{{ book.title }}</h3>
              </div>
              <div class="book-info">
                <div class="book-author">作者：{{ book.author }}</div>
                <div class="book-desc">{{ book.description }}</div>
                <button class="btn btn-primary btn-small" @click="downloadResource(book.title)">获取电子书</button>
              </div>
            </div>
          </div>
        </div>
        
        <div class="resource-category">
          <h3 class="category-title">🎬 视频教程</h3>
          <div class="video-list">
            <div v-for="video in videos" :key="video.title" class="video-item">
              <div class="video-thumbnail" :style="{ background: video.gradient }">
                <span class="play-icon">▶️</span>
              </div>
              <div class="video-info">
                <h3>{{ video.title }}</h3>
                <div class="video-meta">讲师：{{ video.instructor }} | ⏱️ {{ video.duration }}</div>
                <div class="video-desc">{{ video.description }}</div>
                <div class="video-actions">
                  <button class="btn btn-primary" @click="playVideo(video.title)">开始学习</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const documents = [
  {
    icon: '📋',
    title: '前端开发学习路线图',
    description: '详细的前端开发学习路径和知识点梳理',
    tags: ['前端', '入门', 'PDF']
  },
  {
    icon: '📊',
    title: 'Python数据科学手册',
    description: '数据分析和机器学习必备参考资料',
    tags: ['Python', '数据', 'PDF']
  },
  {
    icon: '🎨',
    title: 'UI设计规范文档',
    description: '企业级UI设计系统和组件规范',
    tags: ['设计', '规范', 'Figma']
  },
  {
    icon: '⚡',
    title: '算法面试宝典',
    description: '常见算法题型总结和解题思路',
    tags: ['算法', '面试', 'LeetCode']
  }
]

const books = [
  {
    title: 'JavaScript高级程序设计',
    author: 'Nicholas C. Zakas',
    description: 'JavaScript经典红宝书，前端开发者必备',
    gradient: 'linear-gradient(135deg,#667eea,#764ba2)'
  },
  {
    title: 'Python编程：从入门到实践',
    author: 'Eric Matthes',
    description: 'Python入门最佳教程，零基础友好',
    gradient: 'linear-gradient(135deg,#f093fb,#f5576c)'
  },
  {
    title: '设计心理学',
    author: '唐纳德·诺曼',
    description: '交互设计经典著作，理解用户心理',
    gradient: 'linear-gradient(135deg,#4facfe,#00f2fe)'
  }
]

const videos = [
  {
    title: 'Vue3核心原理与实战',
    instructor: '张老师',
    duration: '12小时',
    description: '深入讲解Vue3响应式原理、虚拟DOM等核心概念，配合实战项目加深理解。',
    gradient: 'linear-gradient(135deg,#667eea,#764ba2)'
  },
  {
    title: 'TypeScript完全指南',
    instructor: '李老师',
    duration: '8小时',
    description: '从基础类型到高级类型体操，全面掌握TypeScript。',
    gradient: 'linear-gradient(135deg,#3178c6,#4a90d9)'
  }
]

const downloadResource = (title) => {
  const toastEvent = new CustomEvent('showToast', {
    detail: { message: `🔗 正在下载《${title}》...`, type: 'info', duration: 2000 }
  })
  window.dispatchEvent(toastEvent)
}

const playVideo = (title) => {
  const toastEvent = new CustomEvent('showToast', {
    detail: { message: '🎬 视频加载中...', type: 'info' }
  })
  window.dispatchEvent(toastEvent)
  setTimeout(() => {
    const event = new CustomEvent('showToast', {
      detail: { message: '准备好了！祝学习愉快 😊', type: 'success' }
    })
    window.dispatchEvent(event)
  }, 1000)
}
</script>
