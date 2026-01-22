<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()
const loggedIn = ref(true)
function bla() {
  loggedIn.value = !loggedIn.value;
}

const test = ref(["Test", "2", "3"])

const count = ref(0)
const newItem = ref('')

function addItem(item: string){
  item = item.trim();
  test.value.push(item);
  newItem.value = '';
}
</script>

<template>
  <h1>{{ msg }}</h1>

  <div v-if="loggedIn" class="card">
    <div>
      <a>Vrai</a>
    </div> 
    <button type="button" @click="count++">count is {{ count }}</button>
  </div>
  <div v-else>
    <a>Faux</a>
  </div>
  <button
    @click="bla"
    :class="['btn', loggedIn ? 'btn--on' : 'btn--off']"
  >
    IfElse
  </button>


  <div v-for="tes in test">
    {{ tes }}
  </div>
  <div>
    <input
      v-model="newItem"
      placeholder="Ajoute un élément"
      @keyup.enter="newItem.trim() && (test.push(newItem.trim()), newItem='')"
    />
    <button @click=addItem(newItem)>Ajouter</button>
  </div>
</template>

<style scoped>
.btn {
  padding: .5rem .75rem;
  border: 1px solid #d1d5db;
  border-radius: .5rem;
  cursor: pointer;
  transition: background-color .2s ease, color .2s ease, border-color .2s ease;
}
.btn--on {
  background-color: #16a34a; /* vert */
  color: #fff;
  border-color: #16a34a;
}
.btn--off {
  background-color: #e5e7eb; /* gris clair */
  color: #374151;            /* gris foncé */
  border-color: #e5e7eb;
}
.btn--neutral {
  background-color: #f3f4f6;
  color: #111827;
}
.add { margin-top: .5rem; display: flex; gap: .5rem; }
input { padding: .5rem .75rem; border: 1px solid #d1d5db; border-radius: .5rem; }
</style>