<template>
  <div
    class="min-h-screen flex flex-col font-sans transition-colors duration-500 ease-in-out"
    :class="{
      'bg-slate-900 text-white': currentTab === 'barberia',
      'bg-indigo-50 text-slate-900': currentTab === 'lavanderia'
    }"
  >
    <!-- Header -->
    <header
      class="fixed top-0 left-0 w-full z-50 px-6 py-3 backdrop-blur-lg transition-all duration-300"
      :class="currentTab === 'barberia' ? 'bg-transparent text-white' : 'bg-transparent text-slate-800'"
    >
      <div class="max-w-7xl mx-auto flex items-center justify-between">
        <!-- Logo dinámico -->
        <div class="leading-tight text-left">
          <h1 :class="currentTab === 'lavanderia' ? 'text-2xl md:text-3xl font-extrabold tracking-tight' : 'text-2xl font-extrabold tracking-tight'">
            <template v-if="currentTab === 'barberia'">
              <span class="text-amber-400">GUA</span>
              <span class="text-white">SON</span>
            </template>
            <template v-else>
              <span class="text-sky-500">Keylani</span>
              <span class="text-black">Sofia</span>
            </template>
          </h1>
        </div>

        <!-- Navegación desktop -->
        <nav class="hidden md:flex items-center gap-3 pr-6">
          <button
            @click="switchTab('barberia')"
            class="uppercase font-semibold text-sm px-5 py-2 rounded-full transition-colors"
            :class="{
              'bg-amber-400 text-slate-900 hover:bg-amber-300': currentTab === 'barberia',
              'bg-white/10 text-white hover:bg-white/20': currentTab !== 'barberia'
            }"
          >
            💈 Barbería
          </button>
          <button
            @click="switchTab('lavanderia')"
            class="uppercase font-semibold text-sm px-5 py-2 rounded-full transition-colors"
            :class="{
              'bg-sky-500 text-white hover:bg-sky-400': currentTab === 'lavanderia',
              'bg-white/10 text-white hover:bg-white/20': currentTab !== 'lavanderia'
            }"
          >
            💧 Lavandería
          </button>
        </nav>

        <!-- Botón hamburguesa móvil -->
        <div class="md:hidden">
          <button @click="toggleMenu" class="text-3xl focus:outline-none">
            <span v-if="!showMobileMenu">☰</span>
            <span v-else>✖</span>
          </button>
        </div>
      </div>

      <!-- Menú móvil -->
      <transition name="fade">
        <div v-if="showMobileMenu" class="md:hidden mt-2 px-6 space-y-2 text-sm font-semibold">
          <button
            @click="switchTab('barberia')"
            class="block w-full text-left px-4 py-2 rounded bg-amber-400 text-slate-900"
          >
            💈 Barbería
          </button>
          <button
            @click="switchTab('lavanderia')"
            class="block w-full text-left px-4 py-2 rounded bg-sky-500 text-white"
          >
            💧 Lavandería
          </button>
        </div>
      </transition>
    </header>

    <!-- Main -->
    <main class="flex-grow">
      <Transition name="fade" mode="out-in">
        <component :is="currentTab === 'barberia' ? BarbershopView : LaundryView" :key="currentTab" />
      </Transition>
    </main>

    <!-- Footer -->
  <footer
  class="border-t text-gray-400 text-sm py-6 mt-16 px-6 transition-colors duration-300"
  :class="[
    currentTab === 'lavanderia' ? 'bg-indigo-50 border-indigo-100 text-slate-700' : 'bg-slate-900 border-slate-700 text-gray-400'
  ]"
>
  <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-center">
    <p class="mb-2 sm:mb-0">
      Desarrollado por
      <a
        href="https://creatividadvisual.nicepage.io/"
        target="_blank"
        rel="noopener noreferrer"
        :class="currentTab === 'lavanderia' ? 'text-sky-600' : 'text-white'"
        class="font-semibold hover:underline"
      >
        Creatividad Visual
      </a>
    </p>
    <p>
      &copy; 2025
      <span :class="currentTab === 'lavanderia' ? 'text-slate-800' : 'text-white'" class="font-semibold">
        {{ currentTab === 'lavanderia' ? 'Keylani Sofia' : 'GuaSon' }}
      </span>.
      Todos los derechos reservados.
    </p>
  </div>
</footer>

  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import BarbershopView from './views/BarbershopView.vue'
import LaundryView from './views/LaundryView.vue'

const currentTab = ref<'barberia' | 'lavanderia'>('barberia')
const showMobileMenu = ref(false)

function toggleMenu() {
  showMobileMenu.value = !showMobileMenu.value
}

function switchTab(tab: 'barberia' | 'lavanderia') {
  currentTab.value = tab
  showMobileMenu.value = false
  window.scrollTo({ top: 0, behavior: 'smooth' })
}
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
