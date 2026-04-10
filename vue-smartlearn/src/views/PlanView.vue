<script setup lang="ts">
import { ref } from 'vue'

const formData = ref({
  goal: '',
  level: '',
  studyTime: '',
  duration: ''
})

const learningPaths = [
  {
    id: 1,
    title: '🎨 前端开发工程师',
    duration: '6-12个月',
    steps: [
      { number: 1, title: '基础阶段', desc: 'HTML5、CSS3、JavaScript基础' },
      { number: 2, title: '进阶阶段', desc: 'ES6+、响应式设计、前端工程化' },
      { number: 3, title: '框架阶段', desc: 'Vue/React框架、状态管理' },
      { number: 4, title: '实战阶段', desc: '项目实战、性能优化、部署上线' },
    ]
  },
  {
    id: 2,
    title: '💻 全栈开发工程师',
    duration: '12-18个月',
    steps: [
      { number: 1, title: '前端基础', desc: 'HTML、CSS、JavaScript、React/Vue' },
      { number: 2, title: '后端开发', desc: 'Node.js/Python、数据库、API设计' },
      { number: 3, title: '运维部署', desc: 'Linux、Docker、CI/CD' },
      { number: 4, title: '全栈项目', desc: '完整项目开发、架构设计' },
    ]
  },
  {
    id: 3,
    title: '🤖 人工智能工程师',
    duration: '12-24个月',
    steps: [
      { number: 1, title: '编程基础', desc: 'Python编程、数据结构与算法' },
      { number: 2, title: '数学基础', desc: '线性代数、概率统计、微积分' },
      { number: 3, title: '机器学习', desc: '监督学习、无监督学习、深度学习' },
      { number: 4, title: '项目实战', desc: '计算机视觉、NLP、推荐系统' },
    ]
  }
]

const studyTips = [
  {
    icon: '📅',
    title: '制定明确目标',
    desc: '设定清晰的短期和长期学习目标，将大目标分解为可实现的小目标。'
  },
  {
    icon: '⏰',
    title: '保持学习节奏',
    desc: '每天固定时间学习，养成良好的学习习惯，持之以恒最重要。'
  },
  {
    icon: '💪',
    title: '注重实践练习',
    desc: '理论与实践相结合，多做项目练习，在实战中提升技能。'
  },
  {
    icon: '🔄',
    title: '定期复习总结',
    desc: '及时复习所学知识，总结学习经验，巩固学习成果。'
  }
]

const generatePlan = () => {
  alert('学习计划已生成！请查看推荐的学习路径。')
}
</script>

<template>
  <div class="plan-page">
    <!-- 页面标题 -->
    <section class="page-header">
      <div class="container">
        <h1>智能学习计划</h1>
        <p>制定个性化学习路径，高效达成学习目标</p>
      </div>
    </section>

    <!-- 学习计划生成器 -->
    <section class="plan-generator">
      <div class="container">
        <div class="plan-form-card">
          <h2>创建你的专属学习计划</h2>
          <form @submit.prevent="generatePlan">
            <div class="form-group">
              <label for="learningGoal">学习目标</label>
              <select id="learningGoal" v-model="formData.goal" required>
                <option value="">请选择你的学习目标</option>
                <option value="frontend">成为前端开发工程师</option>
                <option value="backend">成为后端开发工程师</option>
                <option value="fullstack">成为全栈开发工程师</option>
                <option value="designer">成为UI/UX设计师</option>
                <option value="data">成为数据分析师</option>
                <option value="ai">成为AI工程师</option>
              </select>
            </div>

            <div class="form-group">
              <label>当前水平</label>
              <div class="radio-group">
                <label>
                  <input type="radio" v-model="formData.level" value="beginner" required>
                  <span>零基础</span>
                </label>
                <label>
                  <input type="radio" v-model="formData.level" value="intermediate">
                  <span>有一定基础</span>
                </label>
                <label>
                  <input type="radio" v-model="formData.level" value="advanced">
                  <span>较为熟练</span>
                </label>
              </div>
            </div>

            <div class="form-group">
              <label for="studyTime">每周学习时间</label>
              <select id="studyTime" v-model="formData.studyTime" required>
                <option value="">请选择每周可投入的学习时间</option>
                <option value="5">5小时以下</option>
                <option value="10">5-10小时</option>
                <option value="20">10-20小时</option>
                <option value="30">20小时以上</option>
              </select>
            </div>

            <div class="form-group">
              <label for="duration">期望完成时间</label>
              <select id="duration" v-model="formData.duration" required>
                <option value="">请选择期望完成时间</option>
                <option value="3">3个月</option>
                <option value="6">6个月</option>
                <option value="12">12个月</option>
                <option value="24">24个月</option>
              </select>
            </div>

            <button type="submit" class="btn btn-primary btn-large">生成学习计划</button>
          </form>
        </div>
      </div>
    </section>

    <!-- 推荐学习路径 -->
    <section class="learning-paths">
      <div class="container">
        <h2 class="section-title">热门学习路径</h2>
        <div class="paths-grid">
          <div v-for="path in learningPaths" :key="path.id" class="path-card">
            <div class="path-header">
              <h3>{{ path.title }}</h3>
              <span class="path-duration">{{ path.duration }}</span>
            </div>
            <div class="path-content">
              <div class="path-steps">
                <div v-for="step in path.steps" :key="step.number" class="step">
                  <div class="step-number">{{ step.number }}</div>
                  <div class="step-info">
                    <h4>{{ step.title }}</h4>
                    <p>{{ step.desc }}</p>
                  </div>
                </div>
              </div>
              <button class="btn btn-secondary">选择此路径</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 学习建议 -->
    <section class="study-tips">
      <div class="container">
        <h2 class="section-title">学习建议</h2>
        <div class="tips-grid">
          <div v-for="(tip, index) in studyTips" :key="index" class="tip-card">
            <div class="tip-icon">{{ tip.icon }}</div>
            <h3>{{ tip.title }}</h3>
            <p>{{ tip.desc }}</p>
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

.plan-generator {
  padding: 4rem 0;
  background: var(--light-bg);
}

.plan-form-card {
  background: var(--white);
  padding: 3rem;
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  max-width: 700px;
  margin: 0 auto;
}

.plan-form-card h2 {
  text-align: center;
  margin-bottom: 2rem;
  color: var(--primary-color);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
  color: var(--text-color);
}

.form-group select {
  width: 100%;
  padding: 0.8rem;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s;
}

.form-group select:focus {
  outline: none;
  border-color: var(--primary-color);
}

.radio-group {
  display: flex;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.radio-group label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
  font-weight: normal;
}

.radio-group input[type="radio"] {
  width: 18px;
  height: 18px;
  accent-color: var(--primary-color);
}

.learning-paths {
  padding: 4rem 0;
}

.section-title {
  text-align: center;
  font-size: 2.2rem;
  margin-bottom: 3rem;
  color: var(--primary-color);
}

.paths-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.path-card {
  background: var(--white);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s, box-shadow 0.3s;
}

.path-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.12);
}

.path-header {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
  padding: 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.path-header h3 {
  font-size: 1.3rem;
  margin: 0;
}

.path-duration {
  background: rgba(255, 255, 255, 0.2);
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-size: 0.9rem;
}

.path-content {
  padding: 1.5rem;
}

.path-steps {
  margin-bottom: 1.5rem;
}

.step {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1rem 0;
  border-bottom: 1px solid #eee;
}

.step:last-child {
  border-bottom: none;
}

.step-number {
  width: 32px;
  height: 32px;
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  flex-shrink: 0;
}

.step-info h4 {
  color: var(--primary-color);
  margin-bottom: 0.3rem;
  font-size: 1rem;
}

.step-info p {
  color: #666;
  font-size: 0.9rem;
  margin: 0;
}

.study-tips {
  padding: 4rem 0;
  background: var(--light-bg);
}

.tips-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.tip-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.tip-card:hover {
  transform: translateY(-5px);
}

.tip-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.tip-card h3 {
  color: var(--primary-color);
  margin-bottom: 1rem;
  font-size: 1.2rem;
}

.tip-card p {
  color: #666;
  line-height: 1.6;
}

.btn {
  display: inline-block;
  padding: 0.8rem 2rem;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s;
  border: none;
  cursor: pointer;
  font-size: 1rem;
}

.btn-primary {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
}

.btn-secondary {
  background: transparent;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.btn-secondary:hover {
  background: var(--primary-color);
  color: var(--white);
}

.btn-large {
  padding: 1rem 3rem;
  font-size: 1.1rem;
  width: 100%;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 2rem;
  }

  .plan-form-card {
    padding: 1.5rem;
  }

  .radio-group {
    flex-direction: column;
    gap: 0.8rem;
  }

  .paths-grid {
    grid-template-columns: 1fr;
  }

  .path-header {
    flex-direction: column;
    gap: 0.5rem;
    text-align: center;
  }
}
</style>
