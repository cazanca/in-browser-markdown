<template>
  <div class="flex items-center justify-between h-[42px] px-4 bg-custom-200 dark:bg-custom-900 text-custom-500 dark:text-custom-400 text-sm tracking-[2px] uppercase font-semibold">
    <h2>{{ title }}</h2>
    <slot />
  </div>
</template>

<script setup>
defineProps({
  title: {
    required: true
  }
})
</script>