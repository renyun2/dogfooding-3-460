<template>
  <div>
    <section class="page-header">
      <div class="container">
        <h1>联系我们</h1>
        <p>有任何问题？我们随时为您服务</p>
      </div>
    </section>

    <section class="contact-cards">
      <div class="container">
        <div class="contact-grid">
          <div class="contact-card">
            <div class="contact-icon">📍</div>
            <h3>公司地址</h3>
            <p>北京市海淀区中关村科技园区<br>智慧大厦A座25层</p>
          </div>
          <div class="contact-card">
            <div class="contact-icon">📞</div>
            <h3>联系电话</h3>
            <p>400-888-8888<br>周一至周日 9:00-21:00</p>
          </div>
          <div class="contact-card">
            <div class="contact-icon">✉️</div>
            <h3>电子邮箱</h3>
            <p>support@smartlearn.com<br>business@smartlearn.com</p>
          </div>
          <div class="contact-card">
            <div class="contact-icon">💬</div>
            <h3>在线客服</h3>
            <p>微信公众号：智慧学习<br>QQ群：123456789</p>
          </div>
        </div>
      </div>
    </section>

    <section class="contact-form-section">
      <div class="container">
        <div class="contact-form-wrapper">
          <div class="form-content">
            <h2>发送消息</h2>
            <p>填写下方表单，我们的工作人员会在24小时内回复您。</p>
            <form class="contact-form" @submit.prevent="handleSubmit">
              <div class="form-row">
                <div class="form-group">
                  <label>姓名</label>
                  <input type="text" v-model="form.name" placeholder="请输入您的姓名" required>
                </div>
                <div class="form-group">
                  <label>邮箱</label>
                  <input type="email" v-model="form.email" placeholder="请输入您的邮箱" required>
                </div>
              </div>
              <div class="form-group">
                <label>主题</label>
                <select v-model="form.subject" required>
                  <option value="">请选择咨询主题</option>
                  <option value="course">课程咨询</option>
                  <option value="payment">支付问题</option>
                  <option value="technical">技术支持</option>
                  <option value="cooperation">商务合作</option>
                  <option value="other">其他问题</option>
                </select>
              </div>
              <div class="form-group">
                <label>留言内容</label>
                <textarea v-model="form.message" rows="5" placeholder="请详细描述您的问题或建议..." required></textarea>
              </div>
              <button type="submit" class="btn btn-primary btn-full">发送消息</button>
            </form>
          </div>
          <div class="map-container">
            <svg width="100%" height="100%" viewBox="0 0 500 420" style="border-radius:10px;display:block" xmlns="http://www.w3.org/2000/svg">
              <defs>
                <linearGradient id="mapBg" x1="0%" y1="0%" x2="100%" y2="100%">
                  <stop offset="0%" style="stop-color:#e8f4fc"/>
                  <stop offset="100%" style="stop-color:#d0e8f7"/>
                </linearGradient>
                <linearGradient id="roadGrad" x1="0%" y1="0%" x2="100%" y2="0%">
                  <stop offset="0%" style="stop-color:#fff"/>
                  <stop offset="50%" style="stop-color:#f5f5f5"/>
                  <stop offset="100%" style="stop-color:#fff"/>
                </linearGradient>
                <filter id="shadow" x="-20%" y="-20%" width="140%" height="140%">
                  <feDropShadow dx="0" dy="2" stdDeviation="3" flood-opacity=".2"/>
                </filter>
                <marker id="arrow" markerWidth="6" markerHeight="6" refX="5" refY="3" orient="auto">
                  <path d="M0,0 L0,6 L6,3 z" fill="#667eea"/>
                </marker>
              </defs>
              <rect width="500" height="420" fill="url(#mapBg)"/>
              <text x="20" y="25" font-size="10" fill="#555" font-weight="500">中关村科技园区地图</text>
              <line x1="400" y1="28" x2="475" y2="28" stroke="#aaa" stroke-width=".5"/>
              <text x="478" y="31" font-size="7" fill="#888">N</text>
              <polygon points="480,22 476,28 484,28" fill="#ff6b6b"/>
              <path d="M0,70 H500" stroke="url(#roadGrad)" stroke-width="10"/>
              <text x="20" y="66" font-size="7" fill="#666">北四环西路</text>
              <path d="M70,70 V420" stroke="url(#roadGrad)" stroke-width="8"/>
              <text x="76" y="85" font-size="7" fill="#666">苏州街</text>
              <path d="M170,70 V420" stroke="url(#roadGrad)" stroke-width="8"/>
              <text x="176" y="85" font-size="7" fill="#666">海淀大街</text>
              <path d="M300,70 V420" stroke="url(#roadGrad)" stroke-width="8"/>
              <text x="306" y="85" font-size="7" fill="#666">中关村大街</text>
              <path d="M420,70 V420" stroke="url(#roadGrad)" stroke-width="8"/>
              <text x="426" y="85" font-size="7" fill="#666">学院路</text>
              <path d="M0,150 H500" stroke="url(#roadGrad)" stroke-width="7"/>
              <text x="20" y="146" font-size="7" fill="#666">海淀南路</text>
              <path d="M0,230 H500" stroke="url(#roadGrad)" stroke-width="7"/>
              <text x="20" y="226" font-size="7" fill="#666">知春路</text>
              <path d="M0,320 H500" stroke="url(#roadGrad)" stroke-width="7"/>
              <text x="20" y="316" font-size="7" fill="#666">北三环西路</text>
              <path d="M115,70 V420" stroke="#e0e0e0" stroke-width="3" stroke-dasharray="4,2"/>
              <path d="M235,70 V420" stroke="#e0e0e0" stroke-width="3" stroke-dasharray="4,2"/>
              <path d="M360,70 V420" stroke="#e0e0e0" stroke-width="3" stroke-dasharray="4,2"/>
              <path d="M0,110 H500" stroke="#e0e0e0" stroke-width="2.5" stroke-dasharray="4,2"/>
              <path d="M0,190 H500" stroke="#e0e0e0" stroke-width="2.5" stroke-dasharray="4,2"/>
              <path d="M0,275 H500" stroke="#e0e0e0" stroke-width="2.5" stroke-dasharray="4,2"/>
              <path d="M0,370 H500" stroke="#e0e0e0" stroke-width="2.5" stroke-dasharray="4,2"/>
              <rect x="80" y="165" width="75" height="55" rx="4" fill="#fff" stroke="#ddd" stroke-width="1" filter="url(#shadow)"/>
              <rect x="80" y="165" width="75" height="12" rx="4" fill="#4facfe"/>
              <text x="118" y="175" text-anchor="middle" font-size="8" fill="white" font-weight="bold">腾讯</text>
              <text x="118" y="200" text-anchor="middle" font-size="6" fill="#666">北京总部</text>
              <rect x="185" y="90" width="95" height="48" rx="4" fill="#fff" stroke="#ddd" stroke-width="1" filter="url(#shadow)"/>
              <rect x="185" y="90" width="95" height="12" rx="4" fill="#00d26a"/>
              <text x="233" y="100" text-anchor="middle" font-size="8" fill="white" font-weight="bold">微软亚洲研究院</text>
              <text x="233" y="125" text-anchor="middle" font-size="6" fill="#666">研发中心</text>
              <rect x="315" y="160" width="85" height="62" rx="4" fill="#fff" stroke="#ddd" stroke-width="1" filter="url(#shadow)"/>
              <rect x="315" y="160" width="85" height="12" rx="4" fill="#fe2c55"/>
              <text x="358" y="170" text-anchor="middle" font-size="8" fill="white" font-weight="bold">字节跳动</text>
              <text x="358" y="190" text-anchor="middle" font-size="6" fill="#666">总部大楼</text>
              <text x="358" y="202" text-anchor="middle" font-size="6" fill="#666">30000+员工</text>
              <rect x="100" y="250" width="80" height="50" rx="4" fill="#fff" stroke="#ddd" stroke-width="1" filter="url(#shadow)"/>
              <rect x="100" y="250" width="80" height="12" rx="4" fill="#ff6700"/>
              <text x="140" y="260" text-anchor="middle" font-size="8" fill="white" font-weight="bold">小米科技园</text>
              <text x="140" y="285" text-anchor="middle" font-size="6" fill="#666">科技园区</text>
              <rect x="210" y="260" width="65" height="80" rx="4" fill="#fff" stroke="#ddd" stroke-width="1" filter="url(#shadow)"/>
              <rect x="210" y="260" width="65" height="12" rx="4" fill="#3385ff"/>
              <text x="243" y="270" text-anchor="middle" font-size="8" fill="white" font-weight="bold">百度大厦</text>
              <text x="243" y="295" text-anchor="middle" font-size="6" fill="#666">搜索总部</text>
              <text x="243" y="308" text-anchor="middle" font-size="6" fill="#666">AI研究院</text>
              <text x="243" y="321" text-anchor="middle" font-size="6" fill="#666">阿波罗园区</text>
              <rect x="300" y="280" width="70" height="55" rx="4" fill="#fff" stroke="#ddd" stroke-width="1" filter="url(#shadow)"/>
              <rect x="300" y="280" width="70" height="12" rx="4" fill="#ff0000"/>
              <text x="335" y="290" text-anchor="middle" font-size="8" fill="white" font-weight="bold">京东总部</text>
              <text x="335" y="315" text-anchor="middle" font-size="6" fill="#666">亦庄园区</text>
              <g transform="translate(200, 175)">
                <ellipse cx="30" cy="30" rx="30" ry="15" fill="rgba(102,126,234,.15)"/>
                <ellipse cx="30" cy="30" rx="20" ry="10" fill="rgba(102,126,234,.25)"/>
                <rect x="5" y="0" width="50" height="55" rx="5" fill="url(#roadGrad)" stroke="#667eea" stroke-width="2.5"/>
                <rect x="5" y="0" width="50" height="12" rx="5" fill="linear-gradient(135deg,#667eea,#764ba2)"/>
                <text x="30" y="9" text-anchor="middle" font-size="6" fill="white" font-weight="bold">智慧大厦</text>
                <rect x="10" y="16" width="8" height="5" rx="1" fill="#4facfe" opacity=".6"/>
                <rect x="22" y="16" width="8" height="5" rx="1" fill="#4facfe" opacity=".6"/>
                <rect x="34" y="16" width="8" height="5" rx="1" fill="#4facfe" opacity=".6"/>
                <rect x="10" y="24" width="8" height="5" rx="1" fill="#4facfe" opacity=".6"/>
                <rect x="22" y="24" width="8" height="5" rx="1" fill="#ffd166" opacity=".8"/>
                <rect x="34" y="24" width="8" height="5" rx="1" fill="#4facfe" opacity=".6"/>
                <rect x="10" y="32" width="8" height="5" rx="1" fill="#4facfe" opacity=".6"/>
                <rect x="22" y="32" width="8" height="5" rx="1" fill="#4facfe" opacity=".6"/>
                <rect x="34" y="32" width="8" height="5" rx="1" fill="#06d6a0" opacity=".8"/>
                <rect x="21" y="43" width="18" height="12" rx="2" fill="#333"/>
                <text x="30" y="52" text-anchor="middle" font-size="5" fill="#667eea" font-weight="bold">A座</text>
                <circle cx="30" cy="-5" r="4" fill="#ff6b6b">
                  <animate attributeName="r" values="4;6;4" dur="1.5s" repeatCount="indefinite"/>
                  <animate attributeName="opacity" values="1;.6;1" dur="1.5s" repeatCount="indefinite"/>
                </circle>
                <circle cx="30" cy="-5" r="10" fill="rgba(255,107,107,.3)">
                  <animate attributeName="r" values="8;14;8" dur="1.5s" repeatCount="indefinite"/>
                  <animate attributeName="opacity" values=".5;0;.5" dur="1.5s" repeatCount="indefinite"/>
                </circle>
                <text x="30" y="-12" text-anchor="middle" font-size="6" fill="#ff6b6b" font-weight="bold">您在这里</text>
              </g>
              <path d="M360,195 L230,205" stroke="#667eea" stroke-width="1.5" stroke-dasharray="4,2" marker-end="url(#arrow)"/>
              <text x="365" y="192" font-size="6" fill="#667eea">步行8分钟</text>
              <path d="M360,205 L245,220" stroke="#667eea" stroke-width="1.5" stroke-dasharray="4,2" marker-end="url(#arrow)"/>
              <text x="365" y="208" font-size="6" fill="#667eea">地铁2站</text>
              <g transform="translate(395, 350)">
                <rect width="95" height="60" rx="5" fill="white" stroke="#ddd"/>
                <text x="48" y="14" text-anchor="middle" font-size="7" fill="#333" font-weight="bold">图例</text>
                <line x1="10" y1="26" x2="85" y2="26" stroke="url(#roadGrad)" stroke-width="4"/>
                <text x="90" y="29" font-size="6" fill="#666">主干道</text>
                <rect x="10" y="36" width="18" height="12" rx="2" fill="#fff" stroke="#ddd"/>
                <rect x="10" y="36" width="18" height="4" rx="2" fill="#667eea"/>
                <text x="35" y="46" font-size="6" fill="#666">企业</text>
                <circle cx="20" cy="56" r="3" fill="#ff6b6b"/>
                <text x="30" y="59" font-size="6" fill="#666">我们的位置</text>
              </g>
              <g transform="translate(10, 350)">
                <rect width="75" height="60" rx="5" fill="white" stroke="#ddd"/>
                <text x="38" y="14" text-anchor="middle" font-size="7" fill="#333" font-weight="bold">交通方式</text>
                <text x="8" y="28" font-size="6">🚇 地铁4号线中关村站</text>
                <text x="8" y="40" font-size="6">🚌 公交302/307路</text>
                <text x="8" y="52" font-size="6">🚗 地下停车场B1-B3</text>
              </g>
            </svg>
          </div>
        </div>
      </div>
    </section>

    <section class="faq-section">
      <div class="container">
        <h2 class="section-title">常见问题</h2>
        <div class="faq-list">
          <div class="faq-item" :class="{active: activeFaq === 0}" @click="toggleFaq(0)">
            <div class="faq-question">
              <span>如何注册成为平台学员？</span>
              <span class="faq-icon">{{ activeFaq === 0 ? '−' : '+' }}</span>
            </div>
            <div class="faq-answer">
              <p>点击页面右上角的"注册"按钮，填写手机号码、邮箱和密码即可完成注册。新用户注册即可获得7天免费VIP体验和50元课程优惠券。我们支持微信、QQ、支付宝等第三方账号快速登录。</p>
            </div>
          </div>
          <div class="faq-item" :class="{active: activeFaq === 1}" @click="toggleFaq(1)">
            <div class="faq-question">
              <span>购买的课程可以观看多长时间？</span>
              <span class="faq-icon">{{ activeFaq === 1 ? '−' : '+' }}</span>
            </div>
            <div class="faq-answer">
              <p>所有付费课程购买后均可永久观看，没有时间限制。课程更新内容也会自动同步到您的账户。同时支持离线下载，在无网络环境下也可正常学习。我们承诺课程终身有效，一次购买终身受益。</p>
            </div>
          </div>
          <div class="faq-item" :class="{active: activeFaq === 2}" @click="toggleFaq(2)">
            <div class="faq-question">
              <span>学习过程中遇到问题如何解决？</span>
              <span class="faq-icon">{{ activeFaq === 2 ? '−' : '+' }}</span>
            </div>
            <div class="faq-answer">
              <p>每个课程都配有专属学习社群和助教答疑服务。您可以在课程评论区提问，也可以在VIP专属群内@助教。工作日2小时内回复，周末24小时内回复。高级VIP学员还可享受1对1专属导师服务。</p>
            </div>
          </div>
          <div class="faq-item" :class="{active: activeFaq === 3}" @click="toggleFaq(3)">
            <div class="faq-question">
              <span>是否支持退款？退款流程是怎样的？</span>
              <span class="faq-icon">{{ activeFaq === 3 ? '−' : '+' }}</span>
            </div>
            <div class="faq-answer">
              <p>购买后7天内，如课程学习进度未超过30%，可申请无理由全额退款。退款流程：进入个人中心→我的订单→申请退款，审核通过后1-3个工作日原路退回。特殊课程请查看具体说明。</p>
            </div>
          </div>
          <div class="faq-item" :class="{active: activeFaq === 4}" @click="toggleFaq(4)">
            <div class="faq-question">
              <span>完成课程后是否颁发证书？</span>
              <span class="faq-icon">{{ activeFaq === 4 ? '−' : '+' }}</span>
            </div>
            <div class="faq-answer">
              <p>完成课程所有章节学习并通过结业考试后，即可获得电子版结业证书。部分职业认证课程还可获得合作企业颁发的技能认证证书，可用于求职简历。优秀学员还可获得名企内推机会。</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const activeFaq = ref(null)

const toggleFaq = (index) => {
  activeFaq.value = activeFaq.value === index ? null : index
}

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const handleSubmit = () => {
  alert('消息已发送！我们会尽快回复您。')
  form.value = { name: '', email: '', subject: '', message: '' }
}
</script>
