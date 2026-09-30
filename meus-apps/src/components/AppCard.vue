<script setup>
defineProps({
  app: { type: Object, required: true },
})
</script>

<template>
  <article class="card">
    <div class="icone">{{ app.icone }}</div>

    <div class="info">
      <h3>{{ app.nome }}</h3>
      <span class="tag">{{ app.categoria }}</span>
      <p>{{ app.descricao }}</p>
      <small>v{{ app.versao }} • {{ app.tamanho }}</small>
    </div>

    <a v-if="app.android" :href="app.android" class="btn" download>⬇ Baixar para Android</a>
    <a
      v-if="app.ios"
      :href="app.ios"
      class="btn btn-outline"
      target="_blank"
      rel="noopener"
    >
      Ver no iOS
    </a>
  </article>
</template>