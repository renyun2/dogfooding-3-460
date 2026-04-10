<template>
  <div class="plan-page">
    <section class="page-header">
      <div class="container">
        <h1>智能学习计划</h1>
        <p>制定个性化学习路径，高效达成学习目标</p>
      </div>
    </section>

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

    <section class="learning-paths">
      <div class="container">
        <h2 class="section-title">热门学习路径</h2>
        <div class="paths-grid">
          <div class="path-card" v-for="path in learningPaths" :key="path.title">
            <div class="path-header">
              <h3>{{ path.title }}</h3>
              <span class="path-duration">{{ path.duration }}</span>
            </div>
            <div class="path-content">
              <div class="path-steps">
                <div class="step" v-for="(step, index) in path.steps" :key="index">
                  <div class="step-number">{{ index + 1 }}</div>
                  <div class="step-info">
                    <h4>{{ step.name }}</h4>
                    <p>{{ step.description }}</p>
                  </div>
                </div>
              </div>
              <button class="btn btn-secondary">选择此路径</button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="study-tips">
      <div class="container">
        <h2 class="section-title">学习建议</h2>
        <div class="tips-grid">
          <div class="tip-card" v-for="tip in tips" :key="tip.title">
            <div class="tip-icon">{{ tip.icon }}</div>
            <h3>{{ tip.title }}</h3>
            <p>{{ tip.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <div v-if="showMessage" class="message-box" :class="messageType">
      <div v-html="messageContent"></div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  goal: '',
  level: '',
  studyTime: '',
  duration: ''
})

const showMessage = ref(false)
const messageType = ref('info')
const messageContent = ref('')

const learningPaths = [
  {
    title: '🎨 前端开发工程师',
    duration: '6-12个月',
    steps: [
      { name: '基础阶段', description: 'HTML5、CSS3、JavaScript基础' },
      { name: '进阶阶段', description: 'ES6+、响应式设计、前端工程化' },
      { name: '框架阶段', description: 'Vue/React框架、状态管理' },
      { name: '实战阶段', description: '项目实战、性能优化、部署上线' }
    ]
  },
  {
    title: '💻 全栈开发工程师',
    duration: '12-18个月',
    steps: [
      { name: '前端基础', description: 'HTML、CSS、JavaScript、React/Vue' },
      { name: '后端开发', description: 'Node.js/Python、数据库、API设计' },
      { name: '运维部署', description: 'Linux、Docker、CI/CD' },
      { name: '全栈项目', description: '完整项目开发、架构设计' }
    ]
  },
  {
    title: '🤖 人工智能工程师',
    duration: '12-24个月',
    steps: [
      { name: '编程基础', description: 'Python编程、数据结构与算法' },
      { name: '数学基础', description: '线性代数、概率统计、微积分' },
      { name: '机器学习', description: '监督学习、无监督学习、深度学习' },
      { name: '项目实战', description: '计算机视觉、NLP、推荐系统' }
    ]
  }
]

const tips = [
  { icon: '📅', title: '制定明确目标', description: '设定清晰的短期和长期学习目标，将大目标分解为可实现的小目标。' },
  { icon: '⏰', title: '保持学习节奏', description: '每天固定时间学习，养成良好的学习习惯，持之以恒最重要。' },
  { icon: '💪', title: '注重实践练习', description: '理论与实践相结合，多做项目练习，在实战中提升技能。' },
  { icon: '🔄', title: '定期复习总结', description: '及时复习所学知识，总结学习经验，巩固学习成果。' }
]

const goalMap = {
  frontend: '前端开发工程师',
  backend: '后端开发工程师',
  fullstack: '全栈开发工程师',
  designer: 'UI/UX设计师',
  data: '数据分析师',
  ai: 'AI工程师'
}

const levelMap = {
  beginner: '零基础',
  intermediate: '有一定基础',
  advanced: '较为熟练'
}

const generatePlan = () => {
  showMessage.value = true
  messageType.value = 'info'
  messageContent.value = '正在生成专属学习计划...'
  
  setTimeout(() => {
    messageContent.value = `
      <h3>🎉 学习计划生成成功！</h3>
      <p><strong>学习目标：</strong>${goalMap[formData.value.goal]}</p>
      <p><strong>当前水平：</strong>${levelMap[formData.value.level]}</p>
      <p><strong>每周学习时间：</strong>${formData.value.studyTime}小时</p>
      <p><strong>预计完成时间：</strong>${formData.value.duration}个月</p>
      <p style="margin-top: 1rem;">我们已为你生成专属学习计划，请查看邮箱获取详细信息。</p>
    `
    messageType.value = 'success'
    
    setTimeout(() => {
      showMessage.value = false
    }, 5000)
  }, 2000)
}
</script>

<style scoped>
.plan-generator {
  padding: 3rem 0;
  background: var(--bg-light);
}

.plan-form-card {
  max-width: 700px;
  margin: 0 auto;
  background: var(--white);
  padding: 3rem;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.plan-form-card h2 {
  text-align: center;
  margin-bottom: 2rem;
  color: var(--text-dark);
}

.learning-paths {
  padding: 5rem 0;
}

.paths-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.path-card {
  background: var(--white);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.path-card:hover {
  transform: translateY(-5px);
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
}

.path-duration {
  background: rgba(255, 255, 255, 0.2);
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-size: 0.9rem;
}

.path-content {
  padding: 2rem;
}

.path-steps {
  margin-bottom: 2rem;
}

.step {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.step-number {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: var(--white);
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  flex-shrink: 0;
}

.step-info h4 {
  margin-bottom: 0.3rem;
  color: var(--text-dark);
}

.step-info p {
  color: var(--text-light);
  font-size: 0.9rem;
}

.study-tips {
  padding: 5rem 0;
  background: var(--bg-light);
}

.tips-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.tip-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.tip-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.tip-card h3 {
  margin-bottom: 0.8rem;
  color: var(--text-dark);
}

.tip-card p {
  color: var(--text-light);
  line-height: 1.6;
}

.message-box {
  position: fixed;
  top: 100px;
  left: 50%;
  transform: translateX(-50%);
  max-width: 500px;
  width: 90%;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 5px 20px rgba(0,0,0,0.2);
  z-index: 10000;
  animation: slideDown 0.3s ease-out;
}

.message-box.success {
  background: #d4edda;
  color: #155724;
  border: 2px solid #c3e6cb;
}

.message-box.info {
  background: #d1ecf1;
  color: #0c5460;
  border: 2px solid #bee5eb;
}

@media (max-width: 768px) {
  .paths-grid {
    grid-template-columns: 1fr;
  }
  
  .plan-form-card {
    padding: 1.5rem;
  }
}
</style>
