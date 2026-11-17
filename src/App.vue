<template>
  <div class="home">
    <div class="bg-animation">
      <div class="orb orb-1" />
      <div class="orb orb-2" />
      <div class="orb orb-3" />
    </div>

    <main class="hero">
      <div class="avatar">L</div>
      <h1 class="title">Lockhart</h1>
      <p class="subtitle">
        <span class="typewriter">{{ typedText }}</span>
        <span class="cursor" :class="{ blink: showCursor }">|</span>
      </p>

      <div class="cards">
        <a href="https://ark.lockhart.ren" class="card">
          <div class="card-icon ak-icon">方</div>
          <div class="card-body">
            <h2 class="card-title">明日方舟公招统计</h2>
            <p class="card-desc">记录与管理你的公开招募数据</p>
          </div>
          <span class="card-arrow">&rarr;</span>
        </a>

        <a href="https://blog.lockhart.ren" class="card">
          <div class="card-icon blog-icon">博</div>
          <div class="card-body">
            <h2 class="card-title">博客</h2>
            <p class="card-desc">记录技术学习与生活</p>
          </div>
          <span class="card-arrow">&rarr;</span>
        </a>

        <a href="https://github.com/LockhartANR" target="_blank" class="card">
          <div class="card-icon gh-icon">G</div>
          <div class="card-body">
            <h2 class="card-title">GitHub</h2>
            <p class="card-desc">开源项目与代码</p>
          </div>
          <span class="card-arrow">&rarr;</span>
        </a>
      </div>
    </main>

    <footer class="footer">
      <span>&copy; {{ year }} Lockhart</span>
    </footer>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const words = ['明日方舟 · 公开招募', '记录每一次高资时刻', 'Welcome to Lockhart']
const typedText = ref('')
const showCursor = ref(true)
const year = new Date().getFullYear()

let wordIndex = 0
let charIndex = 0
let isDeleting = false
let timer = null

function type() {
  const current = words[wordIndex]
  if (isDeleting) {
    typedText.value = current.substring(0, charIndex - 1)
    charIndex--
  } else {
    typedText.value = current.substring(0, charIndex + 1)
    charIndex++
  }

  let speed = isDeleting ? 40 : 100

  if (!isDeleting && charIndex === current.length) {
    speed = 2000  // pause at end
    isDeleting = true
  } else if (isDeleting && charIndex === 0) {
    isDeleting = false
    wordIndex = (wordIndex + 1) % words.length
    speed = 300
  }

  timer = setTimeout(type, speed)
}

onMounted(() => {
  type()
})
</script>
