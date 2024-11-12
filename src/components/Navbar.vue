<template>
  <nav class="h-14 md:h-[64px] bg-custom-800 flex items-center justify-between">
    
    <div class="flex items-center">
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
      <div class="flex items-center">
        <p class="hidden mx-6 lg:inline-block uppercase text-custom-100 tracking-[5px] font-logo">markdown</p>
      <hr class="hidden lg:inline-flex border border-custom-600 min-h-8"/>
      <FileRename />
      </div>

    </div>
    <div class="flex items-center gap-6 pr-4">
      <button class="text-custom-500 w-5 h-5" @click.prevent="emit('confirm-delete')">
        <IconDelete />
      </button>
      <JButton>
        <IconSave/>
        <span class="hidden md:inline-block">Save Changes</span>
      </JButton>
    </div>
  </nav>
</template>

<script setup>
import IconMenu from './icons/IconMenu.vue'
import IconClose from './icons/IconClose.vue'
import IconDelete from './icons/IconDelete.vue';
import IconSave from './icons/IconSave.vue';
import JButton from './JButton.vue';
/* import IconDocument from './icons/IconDocument.vue';
 */import FileRename from './FileRename.vue';

defineProps({
  isNavigationOpen: {
    type: Boolean,
    required: true,
  },
})

const emit = defineEmits(['openNavigation', 'closeNavigation', 'confirm-delete'])
</script>
