<template>
  <section class="banner">
    <div class="slider">
      <div 
        v-for="(slide, index) in slides" 
        :key="index" 
        class="slide" 
        :class="{ active: currentSlide === index }"
      >
        <div class="slide-content">
          <div class="slide-text">
            <h2>{{ slide.title }}</h2>
            <p>{{ slide.description }}</p>
            <router-link :to="slide.link" class="btn btn-primary">
              {{ slide.buttonText }} →
            </router-link>
          </div>
          <div class="slide-illustration" v-html="slide.illustration"></div>
        </div>
      </div>
    </div>
    <div class="slider-controls">
      <button class="prev" @click="prevSlide">‹</button>
      <button class="next" @click="nextSlide">›</button>
    </div>
    <div class="slider-dots">
      <div 
        v-for="(_, index) in slides" 
        :key="index"
        class="dot" 
        :class="{ active: currentSlide === index }"
        @click="goToSlide(index)"
      ></div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
let slideInterval = null

const slides = [
  {
    title: '🎓 开启智慧学习之旅',
    description: '个性化学习路径，助力快速成长',
    link: '/courses',
    buttonText: '立即开始',
    illustration: `
      <svg width="320" height="260" viewBox="0 0 320 260">
        <circle cx="160" cy="130" r="120" fill="rgba(255,255,255,.1)"/>
        <rect x="50" y="185" width="220" height="12" rx="4" fill="rgba(255,255,255,.5)"/>
        <rect x="70" y="197" width="10" height="40" rx="3" fill="rgba(255,255,255,.35)"/>
        <rect x="240" y="197" width="10" height="40" rx="3" fill="rgba(255,255,255,.35)"/>
        <rect x="105" y="115" width="110" height="72" rx="6" fill="rgba(255,255,255,.25)" stroke="rgba(255,255,255,.6)" stroke-width="2"/>
        <rect x="112" y="122" width="96" height="58" rx="3" fill="rgba(20,20,60,.3)"/>
        <rect x="118" y="130" width="55" height="3" rx="1" fill="rgba(255,255,255,.7)"/>
        <rect x="118" y="138" width="40" height="3" rx="1" fill="#a0e9ff"/>
        <rect x="118" y="146" width="65" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
        <rect x="118" y="154" width="35" height="3" rx="1" fill="#ffd166"/>
        <rect x="118" y="162" width="50" height="3" rx="1" fill="rgba(255,255,255,.5)"/>
        <path d="M98 187 L100 185 L220 185 L222 187 Z" fill="rgba(255,255,255,.5)"/>
        <rect x="60" y="158" width="30" height="28" rx="2" fill="rgba(255,255,255,.4)"/>
        <rect x="64" y="162" width="22" height="3" rx="1" fill="rgba(255,255,255,.7)"/>
        <rect x="64" y="170" width="18" height="2" rx="1" fill="rgba(255,255,255,.5)"/>
        <rect x="64" y="176" width="20" height="2" rx="1" fill="rgba(255,255,255,.5)"/>
        <rect x="240" y="162" width="28" height="24" rx="2" fill="rgba(255,255,255,.35)" transform="rotate(-8 254 174)"/>
        <line x1="240" y1="185" x2="252" y2="130" stroke="rgba(255,255,255,.5)" stroke-width="3"/>
        <ellipse cx="252" cy="128" rx="18" ry="8" fill="rgba(255,255,255,.35)"/>
        <ellipse cx="252" cy="128" rx="8" ry="4" fill="rgba(255,240,180,.6)"/>
        <circle cx="160" cy="96" r="18" fill="rgba(255,255,255,.7)"/>
        <circle cx="154" cy="93" r="2.5" fill="#667eea"/>
        <circle cx="166" cy="93" r="2.5" fill="#667eea"/>
        <path d="M155 101 Q160 106 165 101" fill="none" stroke="#667eea" stroke-width="1.5" stroke-linecap="round"/>
        <path d="M140 130 Q140 113 160 113 Q180 113 180 130 L178 185 L142 185Z" fill="rgba(255,255,255,.45)"/>
        <path d="M178 140 Q200 145 195 155" fill="none" stroke="rgba(255,255,255,.6)" stroke-width="4" stroke-linecap="round"/>
        <circle cx="56" cy="60" r="14" fill="rgba(255,255,255,.2)"/>
        <circle cx="56" cy="60" r="8" fill="rgba(255,240,100,.5)"/>
        <text x="56" y="65" text-anchor="middle" font-size="10">💡</text>
        <text x="278" y="68" font-size="14" fill="rgba(255,255,255,.6)">✦</text>
        <text x="292" y="100" font-size="10" fill="rgba(255,255,255,.4)">✦</text>
        <text x="42" y="100" font-size="10" fill="rgba(255,255,255,.4)">✦</text>
      </svg>
    `
  },
  {
    title: '📚 海量优质课程',
    description: '涵盖编程、设计、商业等多个领域',
    link: '/courses',
    buttonText: '浏览课程',
    illustration: `
      <svg width="320" height="260" viewBox="0 0 320 260">
        <circle cx="160" cy="130" r="120" fill="rgba(255,255,255,.08)"/>
        <rect x="30" y="40" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
        <rect x="30" y="40" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
        <text x="88" y="70" text-anchor="middle" font-size="24">💻</text>
        <rect x="40" y="92" width="70" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
        <rect x="40" y="102" width="50" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
        <rect x="40" y="111" width="35" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
        <rect x="40" y="119" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
        <rect x="40" y="119" width="65" height="4" rx="2" fill="#ffd166"/>
        <rect x="158" y="40" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
        <rect x="158" y="40" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
        <text x="216" y="70" text-anchor="middle" font-size="24">🎨</text>
        <rect x="168" y="92" width="70" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
        <rect x="168" y="102" width="55" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
        <rect x="168" y="111" width="40" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
        <rect x="168" y="119" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
        <rect x="168" y="119" width="85" height="4" rx="2" fill="#06d6a0"/>
        <rect x="30" y="142" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
        <rect x="30" y="142" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
        <text x="88" y="172" text-anchor="middle" font-size="24">🐍</text>
        <rect x="40" y="194" width="65" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
        <rect x="40" y="204" width="45" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
        <rect x="40" y="213" width="38" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
        <rect x="40" y="221" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
        <rect x="40" y="221" width="45" height="4" rx="2" fill="#ff6b6b"/>
        <rect x="158" y="142" width="116" height="88" rx="8" fill="rgba(255,255,255,.22)"/>
        <rect x="158" y="142" width="116" height="44" rx="8" fill="rgba(255,255,255,.15)"/>
        <text x="216" y="172" text-anchor="middle" font-size="24">🤖</text>
        <rect x="168" y="194" width="70" height="5" rx="2" fill="rgba(255,255,255,.7)"/>
        <rect x="168" y="204" width="55" height="4" rx="2" fill="rgba(255,255,255,.4)"/>
        <rect x="168" y="213" width="42" height="4" rx="2" fill="rgba(255,255,255,.35)"/>
        <rect x="168" y="221" width="96" height="4" rx="2" fill="rgba(255,255,255,.2)"/>
        <rect x="168" y="221" width="72" height="4" rx="2" fill="#a855f7"/>
        <rect x="110" y="10" width="100" height="26" rx="13" fill="rgba(255,255,255,.3)"/>
        <text x="160" y="28" text-anchor="middle" font-size="12" font-weight="bold" fill="white">500+ 精品课程</text>
      </svg>
    `
  },
  {
    title: '🤖 智能学习计划',
    description: 'AI驱动，为你定制专属学习方案',
    link: '/plan',
    buttonText: '制定计划',
    illustration: `
      <svg width="320" height="260" viewBox="0 0 320 260">
        <circle cx="160" cy="130" r="120" fill="rgba(255,255,255,.08)"/>
        <circle cx="160" cy="120" r="46" fill="rgba(255,255,255,.18)" stroke="rgba(255,255,255,.5)" stroke-width="2"/>
        <circle cx="160" cy="120" r="32" fill="rgba(255,255,255,.25)"/>
        <text x="160" y="113" text-anchor="middle" font-size="16" font-weight="bold" fill="white">AI</text>
        <text x="160" y="133" text-anchor="middle" font-size="9" fill="rgba(255,255,255,.85)">智能分析</text>
        <line x1="160" y1="74" x2="160" y2="50" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <line x1="192" y1="88" x2="210" y2="72" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <line x1="206" y1="120" x2="232" y2="120" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <line x1="192" y1="152" x2="210" y2="170" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <line x1="160" y1="166" x2="160" y2="192" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <line x1="128" y1="152" x2="110" y2="170" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <line x1="114" y1="120" x2="88" y2="120" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <line x1="128" y1="88" x2="110" y2="72" stroke="rgba(255,255,255,.4)" stroke-width="1.5" stroke-dasharray="3,2"/>
        <circle cx="160" cy="44" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="160" y="49" text-anchor="middle" font-size="12">📝</text>
        <circle cx="216" cy="66" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="216" y="71" text-anchor="middle" font-size="12">💻</text>
        <circle cx="240" cy="120" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="240" y="125" text-anchor="middle" font-size="12">⚡</text>
        <circle cx="216" cy="175" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="216" y="180" text-anchor="middle" font-size="12">🎯</text>
        <circle cx="160" cy="198" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="160" y="203" text-anchor="middle" font-size="12">🏆</text>
        <circle cx="104" cy="175" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="104" y="180" text-anchor="middle" font-size="12">🎨</text>
        <circle cx="80" cy="120" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="80" y="125" text-anchor="middle" font-size="12">🔬</text>
        <circle cx="104" cy="66" r="14" fill="rgba(255,255,255,.3)"/>
        <text x="104" y="71" text-anchor="middle" font-size="12">📊</text>
        <text x="28" y="50" font-size="16" fill="rgba(255,255,255,.5)">✦</text>
        <text x="282" y="50" font-size="12" fill="rgba(255,255,255,.4)">✦</text>
        <text x="288" y="195" font-size="16" fill="rgba(255,255,255,.4)">✦</text>
      </svg>
    `
  }
]

const goToSlide = (n) => {
  if (n >= slides.length) {
    currentSlide.value = 0
  } else if (n < 0) {
    currentSlide.value = slides.length - 1
  } else {
    currentSlide.value = n
  }
}

const nextSlide = () => goToSlide(currentSlide.value + 1)
const prevSlide = () => goToSlide(currentSlide.value - 1)

const startSlideShow = () => {
  slideInterval = setInterval(() => {
    nextSlide()
  }, 5000)
}

const stopSlideShow = () => {
  clearInterval(slideInterval)
}

onMounted(() => {
  startSlideShow()
})

onUnmounted(() => {
  stopSlideShow()
})
</script>
