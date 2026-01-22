<template>
    <article class="card">
    <header class="card__header"><slot name="header" /></header>
    <section class="card__body"><slot /></section>
    <footer class="card__footer"><slot name="footer" /></footer>
    </article>
</template>


<style scoped>
.card { border: 1px solid #ddd; border-radius: var(--brand-radius); padding: 12px; }
.card__header { font-weight: 600; margin-bottom: 8px; }
.card__footer { margin-top: 8px; opacity: .8; }
</style>