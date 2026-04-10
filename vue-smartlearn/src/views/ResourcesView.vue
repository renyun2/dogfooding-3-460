<script setup lang="ts">
const devTools = [
  { icon: '💻', title: 'Visual Studio Code', desc: '微软开发的免费代码编辑器，功能强大，插件丰富，支持多种编程语言。', tags: ['编辑器', '免费'] },
  { icon: '🎨', title: 'Figma', desc: '在线协作设计工具，用于UI/UX设计、原型制作和团队协作。', tags: ['设计', '免费'] },
  { icon: '📦', title: 'Git', desc: '分布式版本控制系统，用于代码管理和团队协作开发。', tags: ['版本控制', '开源'] },
  { icon: '🐳', title: 'Docker', desc: '容器化平台，简化应用部署和环境配置，提高开发效率。', tags: ['容器', '开源'] },
]

const learningSites = [
  { name: 'MDN Web Docs', content: 'Web开发文档', feature: '权威、全面、中文支持', price: '免费' },
  { name: 'GitHub', content: '代码托管与协作', feature: '开源项目、学习案例丰富', price: '免费' },
  { name: 'Stack Overflow', content: '编程问答社区', feature: '问题解答全面及时', price: '免费' },
  { name: 'Coursera', content: '在线课程平台', feature: '大学级课程、证书认证', price: '部分免费' },
  { name: 'LeetCode', content: '算法练习平台', feature: '面试准备、刷题必备', price: '部分免费' },
  { name: 'FreeCodeCamp', content: '编程学习平台', feature: '项目驱动、完全免费', price: '免费' },
]

const books = [
  { title: 'JavaScript高级程序设计', author: 'Nicholas C. Zakas', desc: 'JS开发者必读经典，深入理解JavaScript核心概念和高级特性。', bg: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)' },
  { title: 'Python编程：从入门到实践', author: 'Eric Matthes', desc: '适合零基础学习者，通过实践项目快速掌握Python编程。', bg: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)' },
  { title: '深入理解计算机系统', author: 'Randal E. Bryant', desc: '计算机科学经典教材，深入理解计算机系统底层原理。', bg: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)' },
  { title: '设计心理学', author: 'Don Norman', desc: 'UI/UX设计必读，理解用户心理，创造优秀的用户体验。', bg: 'linear-gradient(135deg, #fa709a 0%, #fee140 100%)' },
]

const videos = [
  { title: '前端开发完整学习路线', meta: '📹 120集 | ⏱️ 60小时 | 👥 15,234人观看', desc: '从HTML/CSS基础到Vue/React框架，系统化学习前端开发全流程。', bg: 'linear-gradient(135deg, #667eea 0%, #764ba2 100%)' },
  { title: 'Python数据分析实战教程', meta: '📹 80集 | ⏱️ 40小时 | 👥 12,891人观看', desc: '使用Pandas、NumPy等库进行数据处理、分析和可视化实战。', bg: 'linear-gradient(135deg, #f093fb 0%, #f5576c 100%)' },
  { title: 'UI设计零基础入门到精通', meta: '📹 60集 | ⏱️ 30小时 | 👥 9,567人观看', desc: '学习Figma工具使用、设计原则、配色技巧，打造专业作品集。', bg: 'linear-gradient(135deg, #4facfe 0%, #00f2fe 100%)' },
]
</script>

<template>
  <div class="resources-page">
    <!-- 页面标题 -->
    <section class="page-header">
      <div class="container">
        <h1>学习资源</h1>
        <p>精选优质学习资料，助力高效学习</p>
      </div>
    </section>

    <!-- 资源分类 -->
    <section class="resources-section">
      <div class="container">
        <!-- 开发工具 -->
        <div class="resource-category">
          <h2 class="category-title">🛠️ 开发工具推荐</h2>
          <div class="resource-grid">
            <div v-for="tool in devTools" :key="tool.title" class="resource-card">
              <div class="resource-icon">{{ tool.icon }}</div>
              <h3>{{ tool.title }}</h3>
              <p>{{ tool.desc }}</p>
              <div class="resource-tags">
                <span v-for="tag in tool.tags" :key="tag" class="tag">{{ tag }}</span>
              </div>
              <a href="#" class="resource-link">访问官网 →</a>
            </div>
          </div>
        </div>

        <!-- 学习网站 -->
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
              <tr v-for="site in learningSites" :key="site.name">
                <td><strong>{{ site.name }}</strong></td>
                <td>{{ site.content }}</td>
                <td>{{ site.feature }}</td>
                <td>{{ site.price }}</td>
                <td><a href="#" class="btn-link">访问</a></td>
              </tr>
            </tbody>
          </table>
        </div>

        <!-- 电子书籍 -->
        <div class="resource-category">
          <h2 class="category-title">📚 推荐书籍</h2>
          <div class="books-grid">
            <div v-for="book in books" :key="book.title" class="book-card">
              <div class="book-cover" :style="{ background: book.bg }">
                <div class="book-title">{{ book.title }}</div>
              </div>
              <div class="book-info">
                <p class="book-author">作者：{{ book.author }}</p>
                <p class="book-desc">{{ book.desc }}</p>
                <button class="btn btn-small">查看详情</button>
              </div>
            </div>
          </div>
        </div>

        <!-- 视频教程 -->
        <div class="resource-category">
          <h2 class="category-title">🎥 视频教程推荐</h2>
          <div class="video-list">
            <div v-for="video in videos" :key="video.title" class="video-item">
              <div class="video-thumbnail" :style="{ background: video.bg }">
                <div class="play-icon">▶</div>
              </div>
              <div class="video-info">
                <h3>{{ video.title }}</h3>
                <p class="video-meta">{{ video.meta }}</p>
                <p class="video-desc">{{ video.desc }}</p>
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

.resources-section {
  padding: 3rem 0;
}

.resource-category {
  margin-bottom: 4rem;
}

.category-title {
  font-size: 1.8rem;
  margin-bottom: 2rem;
  color: var(--text-dark);
  padding-bottom: 0.5rem;
  border-bottom: 2px solid var(--primary-color);
  display: inline-block;
}

.resource-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 2rem;
}

.resource-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s, box-shadow 0.3s;
  text-align: center;
}

.resource-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.12);
}

.resource-icon {
  font-size: 3.5rem;
  margin-bottom: 1rem;
}

.resource-card h3 {
  color: var(--text-dark);
  margin-bottom: 0.8rem;
  font-size: 1.2rem;
}

.resource-card p {
  color: var(--text-light);
  line-height: 1.6;
  margin-bottom: 1rem;
}

.resource-tags {
  display: flex;
  gap: 0.5rem;
  justify-content: center;
  margin-bottom: 1rem;
}

.tag {
  background: var(--light-bg);
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
  border-collapse: collapse;
  background: var(--white);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
}

.resource-table th,
.resource-table td {
  padding: 1.2rem;
  text-align: left;
  border-bottom: 1px solid #eee;
}

.resource-table th {
  background: var(--primary-color);
  color: var(--white);
  font-weight: 600;
}

.resource-table tr:hover {
  background: var(--light-bg);
}

.btn-link {
  display: inline-block;
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
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 2rem;
}

.book-card {
  background: var(--white);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.book-card:hover {
  transform: translateY(-5px);
}

.book-cover {
  height: 160px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
}

.book-title {
  color: var(--white);
  font-size: 1.1rem;
  font-weight: bold;
  text-align: center;
  line-height: 1.4;
}

.book-info {
  padding: 1.5rem;
}

.book-author {
  color: var(--primary-color);
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

.book-desc {
  color: var(--text-light);
  font-size: 0.9rem;
  line-height: 1.6;
  margin-bottom: 1rem;
}

.video-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.video-item {
  display: flex;
  gap: 1.5rem;
  background: var(--white);
  padding: 1.5rem;
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.video-item:hover {
  transform: translateX(5px);
}

.video-thumbnail {
  width: 200px;
  height: 120px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.play-icon {
  width: 50px;
  height: 50px;
  background: rgba(255, 255, 255, 0.9);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  color: var(--primary-color);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.video-info {
  flex: 1;
}

.video-info h3 {
  color: var(--text-dark);
  margin-bottom: 0.5rem;
  font-size: 1.2rem;
}

.video-meta {
  color: var(--text-light);
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
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

.btn {
  display: inline-block;
  padding: 0.6rem 1.2rem;
  border-radius: 20px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s;
  border: none;
  cursor: pointer;
  font-size: 0.9rem;
}

.btn-primary {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
}

.btn-outline {
  background: transparent;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.btn-outline:hover {
  background: var(--primary-color);
  color: var(--white);
}

.btn-small {
  padding: 0.5rem 1rem;
  font-size: 0.85rem;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 2rem;
  }

  .resource-grid {
    grid-template-columns: 1fr;
  }

  .resource-table {
    font-size: 0.85rem;
  }

  .resource-table th,
  .resource-table td {
    padding: 0.8rem;
  }

  .books-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .video-item {
    flex-direction: column;
  }

  .video-thumbnail {
    width: 100%;
    height: 160px;
  }

  .video-actions {
    flex-wrap: wrap;
  }
}

@media (max-width: 480px) {
  .books-grid {
    grid-template-columns: 1fr;
  }
}
</style>
