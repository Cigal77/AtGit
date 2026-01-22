<script setup lang="ts">
import { ref } from 'vue';


const props = defineProps<{ start: number }>();
const emit = defineEmits<{ (e: 'update', value: number): void }>();


const count = ref(props.start);


function inc() { count.value++; emit('update', count.value); }
function dec() { count.value--; emit('update', count.value); }
</script>


<template>
<div class="counter">
<button @click="dec">-1</button>
<span aria-live="polite" style="margin:0 8px">{{ count }}</span>
<button @click="inc">+1</button>
</div>
</template>


<style scoped>
.counter button { padding: .4rem .6rem; }
</style>