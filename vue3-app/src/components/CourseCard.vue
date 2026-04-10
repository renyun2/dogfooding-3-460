<template>
  <div class="course-card" @click="handleClick">
    <div 
      class="course-image" 
      :style="{ background: course.gradient }"
      v-html="course.svg"
    ></div>
    <div class="course-info">
      <h3>{{ course.title }}</h3>
      <p class="course-desc">{{ course.description }}</p>
      <div class="course-meta">
        <span class="course-level">{{ course.level }}</span>
        <span class="course-students">👥 {{ course.students }}人学习</span>
      </div>
      <router-link to="/courses" class="btn btn-secondary">查看详情 →</router-link>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  course: {
    type: Object,
    required: true
  }
})

const handleClick = () => {
  const toastEvent = new CustomEvent('showToast', {
    detail: { 
      message: `📖 正在进入《${props.course.title}》...`, 
      type: 'success',
      duration: 3000
    }
  })
  window.dispatchEvent(toastEvent)
}
</script>
