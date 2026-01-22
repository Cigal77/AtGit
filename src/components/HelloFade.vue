<script setup>
import { ref } from 'vue'
const show = ref(true)
</script>

<template>
  <button @click="show = !show">{{ show ? 'Hide' : 'Show' }}</button>

  <transition name="fade" mode="out-in" appear>
    <div v-if="show" class="card">Hello with transition ✨</div>
  </transition>
</template>

<style scoped>
.card { padding:16px; border:1px solid #ddd; border-radius:12px; box-shadow:0 6px 20px rgba(0,0,0,.06); }
.fade-enter-from { opacity: 0; transform: translateY(8px); }
.fade-enter-active, .fade-leave-active { transition: all 250ms ease; }
.fade-enter-to { opacity: 1; transform: translateY(0); }
.fade-leave-from { opacity: 1; transform: translateY(0); }
.fade-leave-to { opacity: 0; transform: translateY(-8px); }
</style>
