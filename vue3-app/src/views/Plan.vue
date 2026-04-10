<template>
  <div class="plan">
    <div class="page-header">
      <div class="container">
        <h1>学习计划</h1>
        <p>AI为你定制专属学习方案</p>
      </div>
    </div>
    
    <section class="plan-generator">
      <div class="container">
        <div class="plan-form-card">
          <h2>🎯 生成你的专属学习计划</h2>
          <form @submit.prevent="submitForm" id="planForm">
            <div class="form-group">
              <label for="learningGoal">学习目标</label>
              <select id="learningGoal" v-model="formData.goal">
                <option value="">请选择学习目标</option>
                <option value="frontend">前端开发工程师</option>
                <option value="backend">后端开发工程师</option>
                <option value="fullstack">全栈开发工程师</option>
                <option value="designer">UI/UX设计师</option>
                <option value="data">数据分析师</option>
                <option value="ai">AI工程师</option>
              </select>
            </div>
            
            <div class="form-group">
              <label>当前水平</label>
              <div class="radio-group">
                <label>
                  <input type="radio" name="level" value="beginner" v-model="formData.level">
                  <span>零基础</span>
                </label>
                <label>
                  <input type="radio" name="level" value="intermediate" v-model="formData.level">
                  <span>有一定基础</span>
                </label>
                <label>
                  <input type="radio" name="level" value="advanced" v-model="formData.level">
                  <span>较为熟练</span>
                </label>
              </div>
            </div>
            
            <div class="form-group">
              <label for="studyTime">每周学习时间</label>
              <select id="studyTime" v-model="formData.studyTime">
                <option value="">请选择学习时间</option>
                <option value="5">5小时以下</option>
                <option value="10">5-10小时</option>
                <option value="20">10-20小时</option>
                <option value="30">20小时以上</option>
              </select>
            </div>
            
            <div class="form-group">
              <label for="duration">期望完成时间</label>
              <select id="duration" v-model="formData.duration">
                <option value="">请选择完成时间</option>
                <option value="1">1个月</option>
                <option value="3">3个月</option>
                <option value="6">6个月</option>
                <option value="12">1年</option>
              </select>
            </div>
            
            <button type="submit" class="btn btn-primary btn-large" style="width:100%;margin-top:1rem;">
              🚀 生成学习计划
            </button>
          </form>
        </div>
      </div>
    </section>
    
    <section class="learning-paths">
      <div class="container">
        <h2 class="section-title">推荐学习路径</h2>
        <div class="paths-grid">
          <div class="path-card">
            <div class="path-header">
              <h3>💻 前端开发路径</h3>
              <span class="path-duration">6个月</span>
            </div>
            <div class="path-content">
              <div class="path-steps">
                <div class="step">
                  <div class="step-number">1</div>
                  <div class="step-info">
                    <h4>HTML/CSS基础</h4>
                    <p>掌握页面结构和样式设计</p>
                  </div>
                </div>
                <div class="step">
                  <div class="step-number">2</div>
                  <div class="step-info">
                    <h4>JavaScript进阶</h4>
                    <p>深入理解JS核心概念</p>
                  </div>
                </div>
                <div class="step">
                  <div class="step-number">3</div>
                  <div class="step-info">
                    <h4>Vue/React框架</h4>
                    <p>掌握主流前端框架</p>
                  </div>
                </div>
              </div>
              <button class="btn btn-primary" style="width:100%;" @click="selectPath('前端开发')">选择此路径</button>
            </div>
          </div>
          
          <div class="path-card">
            <div class="path-header">
              <h3>🐍 Python全栈路径</h3>
              <span class="path-duration">8个月</span>
            </div>
            <div class="path-content">
              <div class="path-steps">
                <div class="step">
                  <div class="step-number">1</div>
                  <div class="step-info">
                    <h4>Python基础</h4>
                    <p>掌握Python核心语法</p>
                  </div>
                </div>
                <div class="step">
                  <div class="step-number">2</div>
                  <div class="step-info">
                    <h4>Django/FastAPI</h4>
                    <p>后端框架实战开发</p>
                  </div>
                </div>
                <div class="step">
                  <div class="step-number">3</div>
                  <div class="step-info">
                    <h4>数据库与部署</h4>
                    <p>数据存储与项目上线</p>
                  </div>
                </div>
              </div>
              <button class="btn btn-primary" style="width:100%;" @click="selectPath('Python全栈')">选择此路径</button>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  goal: '',
  level: 'beginner',
  studyTime: '',
  duration: ''
})

const submitForm = () => {
  if (!formData.value.goal || !formData.value.studyTime || !formData.value.duration) {
    showToast('请填写完整信息', 'error')
    return
  }
  
  showToast('🎯 正在生成专属学习计划...', 'success', 4000)
  
  setTimeout(() => {
    showToast('学习计划已生成！请查看邮箱获取详细信息 📧', 'success', 5000)
  }, 1500)
}

const selectPath = (pathName) => {
  showToast(`🎯 你选择了${pathName}学习路径`, 'success', 3000)
  setTimeout(() => {
    showToast('正在生成你的专属学习计划... ⏳', 'info', 3000)
  }, 1000)
}

const showToast = (message, type, duration = 3000) => {
  const toastEvent = new CustomEvent('showToast', { 
    detail: { message, type, duration } 
  })
  window.dispatchEvent(toastEvent)
}
</script>
