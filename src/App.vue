<template>
  <main
    class="max-h-screen h-screen overflow-hidden flex flex-shrink-0 transition-colors duration-300"
  >
    <Sidebar :is-navigation-open="isNavigationOpen" />
    <section class="flex-shrink-0 w-screen h-full">
      <Navbar
        :is-navigation-open="isNavigationOpen"
        @open-navigation="openNavigation"
        @close-navigation="closeNavigation"
      />
    </section>
  </main>
</template>

<script setup>
import { ref, provide } from 'vue'
import { useDark } from '@vueuse/core'

import Sidebar from './components/Sidebar.vue'
import Navbar from './components/Navbar.vue'

const isDark = useDark()

const isNavigationOpen = ref(true)

const openNavigation = () => {
  isNavigationOpen.value = true
}
const closeNavigation = () => {
  isNavigationOpen.value = false
}
provide('isDark', isDark)
</script>
