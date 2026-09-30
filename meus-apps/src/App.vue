<script setup>
import { ref, computed } from 'vue'
import { apps } from './data/apps'
import AppCard from './components/AppCard.vue'
import NavBar from './components/NavBar.vue'

const busca = ref('')
const categoria = ref('Todos')
const categorias = ['Todos', ...new Set(apps.map((a) => a.categoria))]

const filtrados = computed(() =>
  apps.filter(
    (a) =>
      (categoria.value === 'Todos' || a.categoria === categoria.value) &&
      a.nome.toLowerCase().includes(busca.value.toLowerCase())
  )
)

</script>

<template>
  <NavBar />
  <header id="inicio" class="hero">
    <div class="container">
      <h1><span class="gradiente">Aplicativos</span> para facilitar seu dia a dia!</h1>
      <p>Baixe e instale as versões mais recentes dos aplicativos desenvolvidos para você.</p>
      <a href="#apps" class="btn">Ver aplicativos</a>
    </div>
  </header>
  <main id="apps" class="container">
    <div class="filtros">
      <input v-model="busca" type="search" placeholder="Buscar aplicativo..." />
      <button
        v-for="c in categorias"
        :key="c"
        class="chip"
        :class="{ ativo: c === categoria }"
        @click="categoria = c"
      >
        {{ c }}
      </button>
    </div>

    <div class="grid">
      <AppCard v-for="app in filtrados" :key="app.id" :app="app" />
    </div>

    <p v-if="!filtrados.length" class="vazio">Nenhum aplicativo encontrado.</p>
  </main>

    <section id="sobre" class="secao">
    <div class="container">
      <h2>Sobre</h2>
      <p>
        Sou desenvolvedor de aplicativos e crio soluções sob medida para o seu negócio.
        Cada app é feito com Flutter, com foco em desempenho e facilidade de uso.
      </p>
    </div>
  </section>

  <section id="contato" class="secao">
    <div class="container">
      <h2>Contato</h2>
      <p>Precisa de um aplicativo ou de suporte? Fale comigo.</p>
      <a href="mailto:seuemail@exemplo.com" class="btn">Enviar e-mail</a>
    </div>
  </section>

  <footer>
    <div class="container">
      <p>© 2026 • Seu Nome — Desenvolvedor de Aplicativos</p>
    </div>
  </footer>
</template>
