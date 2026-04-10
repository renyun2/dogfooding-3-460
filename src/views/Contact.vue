<template>
  <div class="contact-page">
    <section class="page-header">
      <div class="container">
        <h1>联系我们</h1>
        <p>我们随时准备为你提供帮助</p>
      </div>
    </section>

    <section class="contact-info-section">
      <div class="container">
        <div class="contact-cards">
          <div class="contact-card" v-for="info in contactInfo" :key="info.title">
            <div class="contact-icon">{{ info.icon }}</div>
            <h3>{{ info.title }}</h3>
            <p>{{ info.value }}</p>
            <p class="contact-desc">{{ info.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <section class="contact-form-section">
      <div class="container">
        <div class="form-container">
          <div class="form-header">
            <h2>发送消息</h2>
            <p>填写以下表单，我们会尽快与你联系</p>
          </div>
          
          <form @submit.prevent="submitForm" class="contact-form">
            <div class="form-row">
              <div class="form-group">
                <label for="name">姓名 <span class="required">*</span></label>
                <input type="text" id="name" v-model="formData.name" placeholder="请输入你的姓名" required>
              </div>
              
              <div class="form-group">
                <label for="email">邮箱 <span class="required">*</span></label>
                <input type="email" id="email" v-model="formData.email" placeholder="请输入你的邮箱" required>
              </div>
            </div>

            <div class="form-row">
              <div class="form-group">
                <label for="phone">电话</label>
                <input type="tel" id="phone" v-model="formData.phone" placeholder="请输入你的电话（可选）">
              </div>
              
              <div class="form-group">
                <label for="subject">主题 <span class="required">*</span></label>
                <select id="subject" v-model="formData.subject" required>
                  <option value="">请选择咨询主题</option>
                  <option value="course">课程咨询</option>
                  <option value="technical">技术支持</option>
                  <option value="cooperation">商务合作</option>
                  <option value="suggestion">意见建议</option>
                  <option value="other">其他问题</option>
                </select>
              </div>
            </div>

            <div class="form-group">
              <label for="message">消息内容 <span class="required">*</span></label>
              <textarea id="message" v-model="formData.message" rows="6" placeholder="请详细描述你的问题或需求..." required></textarea>
            </div>

            <div class="form-group">
              <label class="checkbox-label">
                <input type="checkbox" v-model="formData.agree" required>
                <span>我已阅读并同意<a href="#">隐私政策</a>和<a href="#">服务条款</a></span>
              </label>
            </div>

            <button type="submit" class="btn btn-primary btn-large" :disabled="submitting">
              {{ submitting ? '发送中...' : '发送消息' }}
            </button>
          </form>

          <div v-if="formMessage" class="form-message" :class="formMessageType">{{ formMessage }}</div>
        </div>
      </div>
    </section>

    <section class="faq-section">
      <div class="container">
        <h2 class="section-title">常见问题</h2>
        <div class="faq-list">
          <div 
            class="faq-item" 
            v-for="(faq, index) in faqs" 
            :key="index"
            :class="{ active: activeFaq === index }"
          >
            <div class="faq-question" @click="toggleFaq(index)">
              <h3>{{ faq.question }}</h3>
              <span class="faq-toggle">{{ activeFaq === index ? '−' : '+' }}</span>
            </div>
            <div class="faq-answer">
              <p>{{ faq.answer }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="map-section">
      <div class="container">
        <h2 class="section-title">找到我们</h2>
        <div class="map-container">
          <svg width="100%" viewBox="0 0 880 400" style="border-radius:10px;display:block">
            <defs>
              <linearGradient id="mapBg" x1="0%" y1="0%" x2="0%" y2="100%">
                <stop offset="0%" style="stop-color:#e8f4fd"/>
                <stop offset="100%" style="stop-color:#d0e8f5"/>
              </linearGradient>
            </defs>
            <rect width="880" height="400" fill="url(#mapBg)" rx="10"/>
            <rect x="0" y="0" width="880" height="400" fill="#e8f5e9" rx="10"/>
            <rect x="60" y="50" width="220" height="120" rx="6" fill="#c8e6c9"/>
            <rect x="600" y="260" width="200" height="110" rx="6" fill="#c8e6c9"/>
            <rect x="0" y="185" width="880" height="28" fill="#b0bec5"/>
            <rect x="0" y="190" width="880" height="18" fill="#cfd8dc"/>
            <line x1="0" y1="199" x2="880" y2="199" stroke="white" stroke-width="1.5" stroke-dasharray="20,12"/>
            <rect x="395" y="0" width="28" height="400" fill="#b0bec5"/>
            <rect x="400" y="0" width="18" height="400" fill="#cfd8dc"/>
            <line x1="409" y1="0" x2="409" y2="400" stroke="white" stroke-width="1.5" stroke-dasharray="20,12"/>
            <rect x="450" y="220" width="100" height="70" rx="5" fill="#667eea"/>
            <line x1="467" y1="220" x2="467" y2="290" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
            <line x1="484" y1="220" x2="484" y2="290" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
            <line x1="501" y1="220" x2="501" y2="290" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
            <line x1="518" y1="220" x2="518" y2="290" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
            <line x1="535" y1="220" x2="535" y2="290" stroke="rgba(255,255,255,.3)" stroke-width="1"/>
            <rect x="458" y="278" width="84" height="14" rx="3" fill="rgba(255,255,255,.25)"/>
            <text x="500" y="289" text-anchor="middle" font-size="8" font-weight="bold" fill="white">智慧学习科技园</text>
            <line x1="500" y1="220" x2="500" y2="204" stroke="#667eea" stroke-width="2"/>
            <circle cx="500" cy="202" r="3" fill="#ffd166"/>
            <rect x="85" y="190" width="80" height="16" rx="3" fill="white" opacity=".8"/>
            <text x="125" y="202" text-anchor="middle" font-size="9" fill="#546e7a">朝阳区主干道</text>
            <g transform="translate(484, 148)">
              <path d="M16 0 Q16 -32 0 -32 Q-16 -32 -16 -48 Q-16 -72 0 -72 Q16 -72 16 -48 Q16 -32 0 -32 Z" fill="#e53935" transform="scale(0.7)"/>
              <circle cy="-34" r="16" fill="#e53935" transform="scale(0.7)"/>
              <circle cy="-34" r="10" fill="white" opacity=".4" transform="scale(0.7)"/>
              <text y="-28" text-anchor="middle" font-size="14" transform="scale(0.7)">📍</text>
            </g>
            <g transform="translate(555, 130)">
              <rect width="120" height="50" rx="8" fill="white" filter="url(#shadow)"/>
              <text x="60" y="18" text-anchor="middle" font-size="9" font-weight="bold" fill="#333">智慧学习平台</text>
              <text x="60" y="32" text-anchor="middle" font-size="7" fill="#666">北京市朝阳区科技园</text>
              <text x="60" y="44" text-anchor="middle" font-size="7" fill="#667eea">查看详情 →</text>
            </g>
          </svg>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  email: '',
  phone: '',
  subject: '',
  message: '',
  agree: false
})

const submitting = ref(false)
const formMessage = ref('')
const formMessageType = ref('')
const activeFaq = ref(null)

const contactInfo = [
  { icon: '📧', title: '邮箱联系', value: 'info@smartlearn.com', description: '我们会在24小时内回复' },
  { icon: '📱', title: '电话咨询', value: '400-888-8888', description: '工作日 9:00-18:00' },
  { icon: '📍', title: '公司地址', value: '北京市朝阳区科技园', description: '欢迎预约来访' },
  { icon: '💬', title: '在线客服', value: '即时聊天支持', description: '7×24小时在线' }
]

const faqs = [
  { question: '如何开始学习课程？', answer: '注册账号后，浏览课程中心选择适合你的课程，点击"立即学习"即可开始。我们建议先完成学习计划评估，让AI为你推荐最适合的学习路径。' },
  { question: '课程费用如何收取？', answer: '我们提供单课程购买和会员订阅两种模式。单课程价格从199元到599元不等，会员可无限制学习所有课程。我们还定期提供优惠活动和限时免费课程。' },
  { question: '是否提供学习证书？', answer: '完成课程学习并通过考核后，你将获得由智慧学习平台颁发的电子证书。该证书可添加到你的简历和LinkedIn档案中，证明你的学习成果。' },
  { question: '学习遇到问题怎么办？', answer: '我们提供多种支持渠道：课程讨论区可与其他学习者交流，在线客服提供即时帮助，还可以预约导师一对一辅导。所有问题都会得到及时解答。' },
  { question: '课程内容会更新吗？', answer: '我们的课程内容会根据技术发展和行业需求持续更新。已购买课程的学员可以免费获取所有更新内容，确保学到的知识始终与时俱进。' },
  { question: '是否提供就业指导服务？', answer: '我们为学员提供简历优化、面试技巧培训、模拟面试等就业服务。部分课程还包含企业内推机会，帮助学员顺利实现职业转型。' }
]

const toggleFaq = (index) => {
  activeFaq.value = activeFaq.value === index ? null : index
}

const submitForm = () => {
  submitting.value = true
  formMessage.value = ''
  
  setTimeout(() => {
    formMessage.value = '感谢你的留言！我们会在24小时内回复你。'
    formMessageType.value = 'success'
    submitting.value = false
    
    formData.value = {
      name: '',
      email: '',
      phone: '',
      subject: '',
      message: '',
      agree: false
    }
    
    setTimeout(() => {
      formMessage.value = ''
    }, 5000)
  }, 1500)
}
</script>

<style scoped>
.contact-info-section {
  padding: 3rem 0;
  background: var(--bg-light);
}

.contact-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.contact-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.contact-card:hover {
  transform: translateY(-5px);
}

.contact-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.contact-card h3 {
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.contact-card p {
  color: var(--text-light);
}

.contact-desc {
  font-size: 0.9rem;
  margin-top: 0.5rem;
}

.contact-form-section {
  padding: 3rem 0;
}

.form-container {
  max-width: 700px;
  margin: 0 auto;
  background: var(--white);
  padding: 3rem;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.form-header {
  text-align: center;
  margin-bottom: 2rem;
}

.form-header h2 {
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.form-header p {
  color: var(--text-light);
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
}

.required {
  color: var(--error-color);
}

.checkbox-label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
}

.checkbox-label a {
  color: var(--primary-color);
}

.form-message {
  margin-top: 1rem;
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
}

.form-message.success {
  background: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.form-message.error {
  background: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.faq-section {
  padding: 5rem 0;
  background: var(--bg-light);
}

.faq-list {
  max-width: 800px;
  margin: 0 auto;
}

.faq-item {
  background: var(--white);
  border-radius: 12px;
  margin-bottom: 1rem;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.faq-question {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem;
  cursor: pointer;
}

.faq-question h3 {
  font-size: 1.1rem;
  color: var(--text-dark);
}

.faq-toggle {
  font-size: 1.5rem;
  color: var(--primary-color);
  font-weight: bold;
}

.faq-answer {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease-out;
}

.faq-item.active .faq-answer {
  max-height: 200px;
}

.faq-answer p {
  padding: 0 1.5rem 1.5rem;
  color: var(--text-light);
  line-height: 1.8;
}

.map-section {
  padding: 5rem 0;
}

.map-container {
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

@media (max-width: 768px) {
  .form-row {
    grid-template-columns: 1fr;
  }
  
  .form-container {
    padding: 1.5rem;
  }
}
</style>
