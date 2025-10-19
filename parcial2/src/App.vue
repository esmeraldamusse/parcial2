<template>
  <header class="topbar">
    <div class="logo">facebook</div>
    <input type="search" class="search" placeholder="Buscar" />
  </header>

  <nav class="tabs">
    <button
      v-for="tab in tabs"
      :key="tab"
      :class="['tab', { active: activeTab === tab }]"
      @click="activeTab = tab"
    >
      {{ tab }}
    </button>
  </nav>

  <main class="layout">
    <aside class="sidebar">
      <section class="profile">
        <img src="/img/perfil.png" alt="Foto de perfil" class="avatar" />
        <h2 class="username">Esmeralda</h2>

        <div class="links">
          <p><strong>Información</strong></p>
          <p>Info</p>

          <p><strong>Amigos</strong></p>
          <div class="friends">
            <img src="/img/perfil1.jpg" alt="Amigo 1" />
            <img src="/img/perfil1.jpg" alt="Amigo 2" />
            <img src="/img/perfil1.jpg" alt="Amigo 3" />
            <img src="/img/perfil1.jpg" alt="Amigo 4" />
            <img src="/img/perfil1.jpg" alt="Amigo 5" />
            <img src="/img/perfil1.jpg" alt="Amigo 6" />
          </div>
          <a href="#">Ver todo</a>
        </div>
      </section>
    </aside>

    <section class="content">
      <component :is="currentView" />
    </section>
  </main>

  <footer class="footer">
    <p>&copy; 2025 Facebook </p>
  </footer>
</template>

<script setup>
import { ref, computed } from 'vue'
import muro from './components/muro.vue'
import info from './components/info.vue'
import fotos from './components/fotos.vue'
import cajas from './components/cajas.vue'

const tabs = ['muro', 'info', 'fotos', 'cajas']
const activeTab = ref('muro')

const currentView = computed(() => {
  switch (activeTab.value) {
    case 'info': return info
    case 'fotos': return fotos
    case 'cajas': return cajas
    default: return muro
  }
})
</script>

<style scoped>
@import './assets/styles.css';
</style>