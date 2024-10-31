<template>
  <nav class="h-14 md:h-[64px] bg-custom-800 flex items-center">
    <div>
      <button
        @click.prevent="emit('openNavigation')"
        v-if="!isNavigationOpen"
        class="w-14 h-14 md:w-[64px] md:h-[64px] flex items-center justify-center text-custom-100 bg-custom-700"
      >
        <IconMenu />
      </button>
      <button
        @click.prevent="emit('closeNavigation')"
        v-else
        class="w-14 h-14 md:w-[64px] md:h-[64px] flex items-center justify-center text-custom-100 bg-custom-700"
      >
        <IconClose />
      </button>
    </div>
    <div>2</div>
  </nav>
</template>

<script setup>
import IconMenu from './icons/IconMenu.vue'
import IconClose from './icons/IconClose.vue'

defineProps({
  isNavigationOpen: {
    type: Boolean,
    required: true,
  },
})

const emit = defineEmits(['openNavigation', 'closeNavigation'])
</script>
