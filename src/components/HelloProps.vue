<script setup lang="ts">
import { ref, computed } from 'vue';
import EmitCounter from './EmitCounter.vue';

type Item = { id: number; label: string; description: string };
const items = ref<Item[]>([
{ id: 1, label: 'Ticket A', description: 'Détail A' },
{ id: 2, label: 'Ticket B', description: 'Détail B' },
{ id: 3, label: 'Ticket C', description: 'Détail C' },
]);


const query = ref('');
const filtered = computed(() => {
const q = query.value.toLowerCase();
return items.value.filter(i => i.label.toLowerCase().includes(q));
});


const selectedId = ref<number | null>(null);
const selected = computed(() => items.value.find(i => i.id === selectedId.value) ?? null);


const score = ref(0);
</script>


<template>
<div class="grid">
<aside>
<input v-model="query" placeholder="Filtrer…" aria-label="Filtrer" />
<ul role="listbox">
<li v-for="i in filtered" :key="i.id">
<button
:aria-selected="i.id === selectedId"
@click="selectedId = i.id"
class="itemBtn">
{{ i.label }}
</button>
</li>
</ul>
</aside>


<section>
<Card v-if="selected">
<template #header>
<div class="row">
<h3>{{ selected.label }}</h3>
<span class="badge">Score: {{ score }}</span>
</div>
</template>


<p>{{ selected.description }}</p>


<template #footer>
<EmitCounter :start="score" @update="v => (score = v)" />
</template>
</Card>


<p v-else>Choisissez un élément dans la liste.</p>
</section>
</div>
</template>


<style scoped>
.grid { display: grid; grid-template-columns: 260px 1fr; gap: 16px; }
@media (max-width: 740px) { .grid { grid-template-columns: 1fr; } }
</style>