<template>
  <div class="background">
    <div class="clock">
      <p>Current Time: {{ currentDateTime }}</p>
    </div>
    <main class="main">
      <hr />
      <h1 class="h1">Hub page for various projects that I am working on</h1>
      <hr />
      <p class="description">
        It is a place where I can keep track of my ideas and projects. I started this project
        *2025/07/08*
      </p>
      <hr />
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

// Date and Time function
const currentDateTime = ref('')
const updateTime = () => {
  currentDateTime.value = new Date().toLocaleString(undefined, {
    weekday: 'short',
    month: 'short',
    day: 'numeric',
    hour: '2-digit',
    hour12: false,
    minute: '2-digit',
    second: '2-digit',
  })
}

let interval: number

onMounted(() => {
  updateTime()
  interval = setInterval(updateTime, 1000)
})

onUnmounted(() => {
  clearInterval(interval)
})

// I'm happy it works :D
</script>

<style scoped>
.h1 {
  text-align: center;
  margin-top: 2rem;
  color: green;
}

.description {
  text-align: center;
  margin-top: 1rem;
  color: rgb(42, 158, 42);
}

hr {
  height: 2px;
  width: 100%;
  background: linear-gradient(to right, transparent, green, transparent);
  border: none;
  margin: 16px;
}

.background {
  background-color: black;
  background-size: cover;
  background-position: center;
  min-height: 100vh;
  width: 100vw;
}
.clock {
  text-align: center;
  margin-top: 2rem;
  color: limegreen;
  font-weight: bold;
  font-size: 1.2rem;
  border-style: line;
  margin-left: 20px;
  margin: 1rem;
}
</style>
