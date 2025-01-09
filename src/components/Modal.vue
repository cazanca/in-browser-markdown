<template>
  <teleport to="body">
    <div v-if="isOpen" class="fixed inset-0 bg-custom-1000 bg-opacity-75 h-screen flex items-center justify-center transition-all duration-300">
      <div class="space-y-4 max-w-[343px] max-h-[218px] p-6 rounded-md bg-custom-100 update-to-git">
        <h4 class="font-bold text-xl font-serif">Delete this document?</h4>
        <p class="font-serif text-sm text-custom-500">Are you sure you want to delete the ‘welcome.md’ document and its contents? This action cannot be reversed.</p>
        <JButton class="w-full" @click.prevent="emit('delete-close')">Confirm & Delete</JButton>
      </div>
    </div>
  </teleport>
</template>

<script setup>
import JButton from './JButton.vue';

defineProps({
  isOpen: {
    type: Boolean,
    required: true
  }
})

const emit = defineEmits(['delete-close'])
</script>
