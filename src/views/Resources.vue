<template>
  <div class="resources-page">
    <section class="page-header">
      <div class="container">
        <h1>学习资源</h1>
        <p>精选优质学习资料，助力高效学习</p>
      </div>
    </section>

    <section class="resources-section">
      <div class="container">
        <div class="resource-category">
          <h2 class="category-title">🛠️ 开发工具推荐</h2>
          <div class="resource-grid">
            <div class="resource-card" v-for="tool in tools" :key="tool.title">
              <div class="resource-icon">{{ tool.icon }}</div>
              <h3>{{ tool.title }}</h3>
              <p>{{ tool.description }}</p>
              <div class="resource-tags">
                <span class="tag" v-for="tag in tool.tags" :key="tag">{{ tag }}</span>
              </div>
              <a href="#" class="resource-link">访问官网 →</a>
            </div>
          </div>
        </div>

        <div class="resource-category">
          <h2 class="category-title">🌐 优质学习网站</h2>
          <table class="resource-table">
            <thead>
              <tr>
                <th>网站名称</th>
                <th>主要内容</th>
                <th>特点</th>
                <th>费用</th>
                <th>链接</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="site in websites" :key="site.name">
                <td><strong>{{ site.name }}</strong></td>
                <td>{{ site.content }}</td>
                <td>{{ site.feature }}</td>
                <td>{{ site.price }}</td>
                <td><a href="#" class="btn-link">访问</a></td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="resource-category">
          <h2 class="category-title">📚 推荐书籍</h2>
          <div class="books-grid">
            <div class="book-card" v-for="book in books" :key="book.title">
              <div class="book-cover" :style="{ background: book.background }">
                <div class="book-title">{{ book.title }}</div>
              </div>
              <div class="book-info">
                <p class="book-author">{{ book.author }}</p>
                <p class="book-desc">{{ book.description }}</p>
                <button class="btn btn-small">查看详情</button>
              </div>
            </div>
          </div>
        </div>

        <div class="resource-category">
          <h2 class="category-title">🎥 视频教程推荐</h2>
          <div class="video-list">
            <div class="video-item" v-for="video in videos" :key="video.title">
              <div class="video-thumbnail" :style="{ background: video.background }">
                <div class="play-icon">▶</div>
              </div>
              <div class="video-info">
                <h3>{{ video.title }}</h3>
                <p class="video-meta">{{ video.meta }}</p>
                <p class="video-desc">{{ video.description }}</p>
                <div class="video-actions">
                  <button class="btn btn-primary btn-small">开始学习</button>
                  <button class="btn btn-outline btn-small">加入收藏</button>
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
const tools = [
  { icon: '💻', title: 'Visual Studio Code', description: '微软开发的免费代码编辑器，功能强大，插件丰富，支持多种编程语言。', tags: ['编辑器', '免费'] },
  { icon: '🎨', title: 'Figma', description: '在线协作设计工具，用于UI/UX设计、原型制作和团队协作。', tags: ['设计', '免费'] },
  { icon: '📦', title: 'Git', description: '分布式版本控制系统，用于代码管理和团队协作开发。', tags: ['版本控制', '开源'] },
  { icon: '🐳', title: 'Docker', description: '容器化平台，简化应用部署和环境配置，提高开发效率。', tags: ['容器', '开源'] }
]

const websites = [
  { name: 'MDN Web Docs', content: 'Web开发文档', feature: '权威、全面、中文支持', price: '免费' },
  { name: 'GitHub', content: '代码托管与协作', feature: '开源项目、学习案例丰富', price: '免费' },
  { name: 'Stack Overflow', content: '编程问答社区', feature: '问题解答全面及时', price: '免费' },
  { name: 'Coursera', content: '在线课程平台', feature: '大学级课程、证书认证', price: '部分免费' },
  { name: 'LeetCode', content: '算法练习平台', feature: '面试准备、刷题必备', price: '部分免费' },
  { name: 'FreeCodeCamp', content: '编程学习平台', feature: '项目驱动、完全免费', price: '免费' }
]

const books = [
  { title: 'JavaScript高级程序设计', author: '作者：Nicholas C. Zakas', description: 'JS开发者必读经典，深入理解JavaScript核心概念和高级特性。', background: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)' },
  { title: 'Python编程：从入门到实践', author: '作者：Eric Matthes', description: '适合零基础学习者，通过实践项目快速掌握Python编程。', background: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)' },
  { title: '深入理解计算机系统', author: '作者：Randal E. Bryant', description: '计算机科学经典教材，深入理解计算机系统底层原理。', background: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)' },
  { title: '设计心理学', author: '作者：Don Norman', description: 'UI/UX设计必读，理解用户心理，创造优秀的用户体验。', background: 'linear-gradient(135deg, #fa709a 0%, #fee140 100%)' }
]

const videos = [
  { title: '前端开发完整学习路线', meta: '📹 120集 | ⏱️ 60小时 | 👥 15,234人观看', description: '从HTML/CSS基础到Vue/React框架，系统化学习前端开发全流程。', background: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)' },
  { title: 'Python数据分析实战教程', meta: '📹 80集 | ⏱️ 40小时 | 👥 12,891人观看', description: '使用Pandas、NumPy等库进行数据处理、分析和可视化实战。', background: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)' },
  { title: 'UI设计零基础入门到精通', meta: '📹 60集 | ⏱️ 30小时 | 👥 9,567人观看', description: '学习Figma工具使用、设计原则、配色技巧，打造专业作品集。', background: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)' }
]
</script>

<style scoped>
.resources-section {
  padding: 3rem 0;
}

.resource-category {
  margin-bottom: 4rem;
}

.category-title {
  font-size: 2rem;
  margin-bottom: 2rem;
  color: var(--text-dark);
}

.resource-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
}

.resource-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.resource-card:hover {
  transform: translateY(-3px);
}

.resource-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.resource-card h3 {
  margin-bottom: 0.8rem;
  color: var(--text-dark);
}

.resource-card p {
  color: var(--text-light);
  line-height: 1.6;
  margin-bottom: 1rem;
}

.resource-tags {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tag {
  background: var(--bg-light);
  padding: 0.3rem 0.8rem;
  border-radius: 15px;
  font-size: 0.85rem;
  color: var(--primary-color);
}

.resource-link {
  color: var(--primary-color);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.3s;
}

.resource-link:hover {
  color: var(--secondary-color);
}

.resource-table {
  width: 100%;
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.resource-table thead {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
}

.resource-table th,
.resource-table td {
  padding: 1rem;
  text-align: left;
}

.resource-table tbody tr {
  border-bottom: 1px solid var(--border-color);
  transition: background 0.3s;
}

.resource-table tbody tr:hover {
  background: var(--bg-light);
}

.btn-link {
  padding: 0.4rem 1rem;
  background: var(--primary-color);
  color: var(--white);
  text-decoration: none;
  border-radius: 5px;
  font-size: 0.9rem;
  transition: background 0.3s;
}

.btn-link:hover {
  background: var(--secondary-color);
}

.books-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.book-card {
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.book-card:hover {
  transform: translateY(-5px);
}

.book-cover {
  height: 250px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
}

.book-title {
  color: var(--white);
  font-size: 1.3rem;
  font-weight: bold;
  text-align: center;
}

.book-info {
  padding: 1.5rem;
}

.book-author {
  color: var(--text-light);
  margin-bottom: 0.5rem;
}

.book-desc {
  color: var(--text-light);
  line-height: 1.6;
  margin-bottom: 1rem;
}

.video-list {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.video-item {
  display: flex;
  gap: 2rem;
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.video-thumbnail {
  width: 300px;
  min-height: 200px;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.play-icon {
  font-size: 3rem;
  color: var(--white);
  opacity: 0.9;
}

.video-info {
  flex: 1;
  padding: 1.5rem;
}

.video-info h3 {
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.video-meta {
  color: var(--text-light);
  margin-bottom: 0.8rem;
}

.video-desc {
  color: var(--text-light);
  line-height: 1.6;
  margin-bottom: 1rem;
}

.video-actions {
  display: flex;
  gap: 1rem;
}

@media (max-width: 768px) {
  .video-item {
    flex-direction: column;
  }
  
  .video-thumbnail {
    width: 100%;
    min-height: 180px;
  }
  
  .resource-table {
    display: block;
    overflow-x: auto;
  }
}
</style>
