<script setup>
import { ref } from 'vue'

const aberto = ref(false)

const links = [
  { texto: 'Início', href: '#inicio' },
  { texto: 'Aplicativos', href: '#apps' },
  { texto: 'Sobre', href: '#sobre' },
  { texto: 'Contato', href: '#contato' },
]

function fechar() {
  aberto.value = false
}
</script>

<template>
  <nav class="navbar">
    <div class="container nav-conteudo">
      <a href="#inicio" class="logo" @click="fechar">
        <span class="logo-icone">▲</span>
        <span class="logo-texto">AppForYou</span>
      </a>

      <button
        class="menu-toggle"
        aria-label="Abrir menu"
        :aria-expanded="aberto"
        @click="aberto = !aberto"
      >
        {{ aberto ? '✕' : '☰' }}
      </button>

      <ul class="nav-links" :class="{ aberto: aberto }">
        <li v-for="l in links" :key="l.href">
          <a :href="l.href" @click="fechar">{{ l.texto }}</a>
        </li>
      </ul>
    </div>
  </nav>
</template>