<script setup lang="ts">
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const submitForm = () => {
  alert('感谢您的留言！我们会尽快与您联系。')
  form.value = { name: '', email: '', subject: '', message: '' }
}

const contactInfo = [
  { icon: '📍', title: '公司地址', content: '北京市海淀区中关村科技园智慧大厦18层' },
  { icon: '📞', title: '客服热线', content: '400-888-9999（周一至周日 9:00-21:00）' },
  { icon: '✉️', title: '电子邮箱', content: 'contact@smartlearn.com' },
  { icon: '🌐', title: '官方网站', content: 'www.smartlearn.com' },
]

const socialLinks = [
  { icon: '💬', name: '微信公众号', desc: '扫码关注获取最新资讯' },
  { icon: '📱', name: '微博', desc: '@智慧学习官方账号' },
  { icon: '💼', name: 'LinkedIn', desc: '智慧学习官方主页' },
  { icon: '🎬', name: 'B站', desc: '智慧学习官方频道' },
]

const faqs = [
  {
    question: '如何购买课程？',
    answer: '您可以通过网站首页或课程页面浏览感兴趣的课程，点击"立即学习"按钮，选择适合的套餐后完成支付即可开始学习。我们支持支付宝、微信支付等多种支付方式。'
  },
  {
    question: '课程购买后可以退款吗？',
    answer: '购买课程后7天内，如果学习进度不超过20%，可以申请全额退款。超过7天或学习进度超过20%的课程不支持退款。具体退款政策请查看服务条款。'
  },
  {
    question: '如何获得学习证书？',
    answer: '完成课程所有章节的学习并通过结业考试后，系统会自动颁发电子证书。您可以在个人中心的"我的证书"页面查看和下载。部分课程还提供纸质证书邮寄服务。'
  },
  {
    question: '企业团购有优惠吗？',
    answer: '是的，我们为企业客户提供团购优惠。10人以上团购可享受8折优惠，50人以上可享受7折优惠，100人以上可定制专属学习方案。请联系企业销售团队获取详细报价。'
  },
]

const offices = [
  { city: '北京总部', address: '北京市海淀区中关村科技园智慧大厦18层', phone: '010-8888-9999' },
  { city: '上海分部', address: '上海市浦东新区张江高科技园区创新大厦12层', phone: '021-6666-8888' },
  { city: '深圳分部', address: '深圳市南山区科技园南区腾讯大厦旁智慧中心', phone: '0755-8888-6666' },
]
</script>

<template>
  <div class="contact-page">
    <!-- 页面标题 -->
    <section class="page-header">
      <div class="container">
        <h1>联系我们</h1>
        <p>随时为您提供帮助与支持</p>
      </div>
    </section>

    <!-- 联系信息卡片 -->
    <section class="contact-info-section">
      <div class="container">
        <div class="contact-grid">
          <div v-for="info in contactInfo" :key="info.title" class="contact-card">
            <div class="contact-icon">{{ info.icon }}</div>
            <h3>{{ info.title }}</h3>
            <p>{{ info.content }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 联系表单和地图 -->
    <section class="contact-main">
      <div class="container">
        <div class="contact-layout">
          <!-- 联系表单 -->
          <div class="contact-form-wrapper">
            <h2>发送消息</h2>
            <p class="form-desc">有任何问题或建议？请填写下方表单，我们会尽快回复您。</p>
            <form class="contact-form" @submit.prevent="submitForm">
              <div class="form-row">
                <div class="form-group">
                  <label for="name">您的姓名 *</label>
                  <input id="name" v-model="form.name" type="text" required placeholder="请输入您的姓名">
                </div>
                <div class="form-group">
                  <label for="email">电子邮箱 *</label>
                  <input id="email" v-model="form.email" type="email" required placeholder="请输入您的邮箱">
                </div>
              </div>
              <div class="form-group">
                <label for="subject">咨询主题 *</label>
                <select id="subject" v-model="form.subject" required>
                  <option value="">请选择咨询主题</option>
                  <option value="course">课程咨询</option>
                  <option value="payment">支付问题</option>
                  <option value="technical">技术支持</option>
                  <option value="cooperation">商务合作</option>
                  <option value="other">其他问题</option>
                </select>
              </div>
              <div class="form-group">
                <label for="message">详细内容 *</label>
                <textarea id="message" v-model="form.message" rows="5" required placeholder="请详细描述您的问题或建议..."></textarea>
              </div>
              <button type="submit" class="submit-btn">发送消息</button>
            </form>
          </div>

          <!-- 地图区域 -->
          <div class="map-wrapper">
            <h2>公司位置</h2>
            <!-- SVG 地图 -->
            <div class="map-container">
              <svg width="100%" height="100%" viewBox="0 0 500 350" style="border-radius:10px;display:block" xmlns="http://www.w3.org/2000/svg">
                <defs>
                  <linearGradient id="mapGrad" x1="0%" y1="0%" x2="100%" y2="100%">
                    <stop offset="0%" style="stop-color:#f8f9ff"/>
                    <stop offset="100%" style="stop-color:#e8ecff"/>
                  </linearGradient>
                  <filter id="shadow" x="-20%" y="-20%" width="140%" height="140%">
                    <feDropShadow dx="0" dy="2" stdDeviation="3" flood-color="rgba(0,0,0,.15)"/>
                  </filter>
                </defs>
                <rect width="500" height="350" fill="url(#mapGrad)"/>
                <!-- 道路网格 -->
                <line x1="50" y1="50" x2="450" y2="50" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="50" y1="120" x2="450" y2="120" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="50" y1="190" x2="450" y2="190" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="50" y1="260" x2="450" y2="260" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="50" y1="330" x2="450" y2="330" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="50" y1="50" x2="50" y2="330" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="150" y1="50" x2="150" y2="330" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="250" y1="50" x2="250" y2="330" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="350" y1="50" x2="350" y2="330" stroke="#d0d4e0" stroke-width="2"/>
                <line x1="450" y1="50" x2="450" y2="330" stroke="#d0d4e0" stroke-width="2"/>
                <!-- 建筑物 -->
                <rect x="70" y="70" width="60" height="40" fill="#c5cae9" rx="3"/>
                <rect x="70" y="70" width="60" height="8" fill="#9fa8da" rx="3"/>
                <rect x="170" y="140" width="50" height="35" fill="#c5cae9" rx="3"/>
                <rect x="170" y="140" width="50" height="6" fill="#9fa8da" rx="3"/>
                <rect x="370" y="90" width="55" height="45" fill="#c5cae9" rx="3"/>
                <rect x="370" y="90" width="55" height="8" fill="#9fa8da" rx="3"/>
                <rect x="80" y="210" width="45" height="35" fill="#c5cae9" rx="3"/>
                <rect x="80" y="210" width="45" height="6" fill="#9fa8da" rx="3"/>
                <rect x="280" y="280" width="50" height="30" fill="#c5cae9" rx="3"/>
                <rect x="280" y="280" width="50" height="6" fill="#9fa8da" rx="3"/>
                <!-- 公园绿地 -->
                <ellipse cx="400" cy="240" rx="35" ry="25" fill="#c8e6c9"/>
                <circle cx="385" cy="230" r="8" fill="#81c784"/>
                <circle cx="405" cy="235" r="10" fill="#66bb6a"/>
                <circle cx="415" cy="250" r="7" fill="#81c784"/>
                <circle cx="390" cy="255" r="9" fill="#4caf50"/>
                <!-- 湖泊 -->
                <ellipse cx="120" cy="290" rx="40" ry="25" fill="#b3e5fc"/>
                <ellipse cx="110" cy="285" rx="15" ry="10" fill="#81d4fa" opacity=".6"/>
                <ellipse cx="130" cy="295" rx="12" ry="8" fill="#4fc3f7" opacity=".5"/>
                <!-- 智慧大厦位置标记 -->
                <g transform="translate(220, 100)">
                  <ellipse cx="30" cy="75" rx="25" ry="8" fill="rgba(102,126,234,.3)"/>
                  <!-- 大厦主体 -->
                  <rect x="10" y="0" width="40" height="75" fill="#667eea" rx="2"/>
                  <rect x="10" y="0" width="40" height="8" fill="#5a6fd6" rx="2"/>
                  <!-- 窗户 -->
                  <rect x="15" y="15" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="27" y="15" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="39" y="15" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="15" y="28" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="27" y="28" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="39" y="28" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="15" y="41" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="27" y="41" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="39" y="41" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="15" y="54" width="8" height="8" fill="#ffd166" rx="1"/>
                  <rect x="27" y="54" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <rect x="39" y="54" width="8" height="8" fill="#a8b5f0" rx="1"/>
                  <!-- 定位标记 -->
                  <circle cx="30" cy="-15" r="18" fill="#f5576c" filter="url(#shadow)"/>
                  <circle cx="30" cy="-15" r="12" fill="white"/>
                  <text x="30" y="-11" text-anchor="middle" font-size="14">📍</text>
                  <path d="M22 3 L30 12 L38 3" fill="#f5576c"/>
                </g>
                <!-- 其他标记点 -->
                <g transform="translate(100, 160)">
                  <circle cx="0" cy="0" r="8" fill="#06d6a0"/>
                  <circle cx="0" cy="0" r="4" fill="white"/>
                </g>
                <g transform="translate(320, 200)">
                  <circle cx="0" cy="0" r="8" fill="#ffd166"/>
                  <circle cx="0" cy="0" r="4" fill="white"/>
                </g>
                <g transform="translate(180, 280)">
                  <circle cx="0" cy="0" r="8" fill="#118ab2"/>
                  <circle cx="0" cy="0" r="4" fill="white"/>
                </g>
                <!-- 图例 -->
                <g transform="translate(20, 20)">
                  <rect x="0" y="0" width="120" height="80" fill="white" rx="5" opacity=".95"/>
                  <circle cx="15" cy="20" r="6" fill="#f5576c"/>
                  <text x="28" y="24" font-size="11" fill="#333">智慧大厦（总部）</text>
                  <circle cx="15" cy="40" r="6" fill="#06d6a0"/>
                  <text x="28" y="44" font-size="11" fill="#333">地铁站</text>
                  <circle cx="15" cy="60" r="6" fill="#ffd166"/>
                  <text x="28" y="64" font-size="11" fill="#333">公交站</text>
                </g>
                <!-- 方向标 -->
                <g transform="translate(450, 20)">
                  <circle cx="20" cy="20" r="18" fill="white" opacity=".9"/>
                  <text x="20" y="10" text-anchor="middle" font-size="10" fill="#333">N</text>
                  <polygon points="20,14 16,24 20,22 24,24" fill="#333"/>
                </g>
              </svg>
            </div>
            <div class="map-info">
              <p><strong>📍 北京总部</strong></p>
              <p>北京市海淀区中关村科技园智慧大厦18层</p>
              <p class="transport">🚇 地铁：4号线中关村站A出口，步行5分钟</p>
              <p class="transport">🚌 公交：302、307、355路中关村南站</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 社交媒体 -->
    <section class="social-section">
      <div class="container">
        <h2 class="section-title">关注我们</h2>
        <div class="social-grid">
          <div v-for="social in socialLinks" :key="social.name" class="social-card">
            <div class="social-icon">{{ social.icon }}</div>
            <h3>{{ social.name }}</h3>
            <p>{{ social.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 常见问题 -->
    <section class="faq-section">
      <div class="container">
        <h2 class="section-title">常见问题</h2>
        <div class="faq-list">
          <div v-for="(faq, index) in faqs" :key="index" class="faq-item">
            <h3 class="faq-question">Q: {{ faq.question }}</h3>
            <p class="faq-answer">A: {{ faq.answer }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 办公地点 -->
    <section class="offices-section">
      <div class="container">
        <h2 class="section-title">全国办公地点</h2>
        <div class="offices-grid">
          <div v-for="office in offices" :key="office.city" class="office-card">
            <h3>{{ office.city }}</h3>
            <p class="office-address">📍 {{ office.address }}</p>
            <p class="office-phone">📞 {{ office.phone }}</p>
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

.contact-info-section {
  padding: 4rem 0;
  background: var(--light-bg);
}

.contact-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.contact-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.contact-card:hover {
  transform: translateY(-5px);
}

.contact-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.contact-card h3 {
  color: var(--text-dark);
  margin-bottom: 0.5rem;
  font-size: 1.1rem;
}

.contact-card p {
  color: var(--text-light);
  font-size: 0.95rem;
  line-height: 1.6;
}

.contact-main {
  padding: 5rem 0;
  background: var(--white);
}

.contact-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
}

.contact-form-wrapper h2,
.map-wrapper h2 {
  font-size: 1.8rem;
  color: var(--text-dark);
  margin-bottom: 0.5rem;
}

.form-desc {
  color: var(--text-light);
  margin-bottom: 2rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  color: var(--text-dark);
  font-weight: 500;
  font-size: 0.95rem;
}

.form-group input,
.form-group select,
.form-group textarea {
  padding: 0.9rem 1rem;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s;
  font-family: inherit;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--primary-color);
}

.form-group textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-btn {
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: var(--white);
  padding: 1rem 2rem;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.3s, box-shadow 0.3s;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
}

.map-container {
  background: var(--light-bg);
  border-radius: 15px;
  overflow: hidden;
  margin-top: 1.5rem;
  height: 320px;
}

.map-info {
  margin-top: 1.5rem;
  padding: 1.5rem;
  background: var(--light-bg);
  border-radius: 10px;
}

.map-info p {
  color: var(--text-light);
  margin-bottom: 0.5rem;
}

.map-info strong {
  color: var(--text-dark);
  font-size: 1.1rem;
}

.transport {
  font-size: 0.9rem;
  color: var(--text-light);
}

.social-section {
  padding: 5rem 0;
  background: var(--light-bg);
}

.section-title {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 3rem;
  color: var(--primary-color);
}

.social-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 2rem;
}

.social-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  text-align: center;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.social-card:hover {
  transform: translateY(-5px);
}

.social-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.social-card h3 {
  color: var(--text-dark);
  margin-bottom: 0.5rem;
}

.social-card p {
  color: var(--text-light);
  font-size: 0.9rem;
}

.faq-section {
  padding: 5rem 0;
  background: var(--white);
}

.faq-list {
  max-width: 900px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.faq-item {
  background: var(--light-bg);
  padding: 1.5rem 2rem;
  border-radius: 12px;
  transition: transform 0.3s;
}

.faq-item:hover {
  transform: translateX(5px);
}

.faq-question {
  color: var(--text-dark);
  font-size: 1.1rem;
  margin-bottom: 0.8rem;
  font-weight: 600;
}

.faq-answer {
  color: var(--text-light);
  line-height: 1.7;
}

.offices-section {
  padding: 5rem 0;
  background: var(--light-bg);
}

.offices-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.office-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s;
}

.office-card:hover {
  transform: translateY(-5px);
}

.office-card h3 {
  color: var(--primary-color);
  font-size: 1.3rem;
  margin-bottom: 1rem;
}

.office-address,
.office-phone {
  color: var(--text-light);
  margin-bottom: 0.5rem;
  line-height: 1.6;
}

@media (max-width: 768px) {
  .page-header h1 {
    font-size: 2rem;
  }

  .contact-layout {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .form-row {
    grid-template-columns: 1fr;
  }

  .map-container {
    height: 250px;
  }

  .social-grid {
    grid-template-columns: repeat(2, 1fr);
  }

  .offices-grid {
    grid-template-columns: 1fr;
  }
}
</style>
