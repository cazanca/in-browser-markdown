<template>
  <div
    class="bg-custom-800 h-14 md:h-[64px] flex items-center gap-x-[11px] max-w-[350px] pl-6"
  >
    <iconDocument class="text-custom-100" />
    <div class="w-[80%] group">
      <p
        class="hidden md:inline-block text-custom-400 font-thin text-[13px] group-hover:text-custom-500"
      >
        Document name
      </p>
      <input
        type="text"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        class="w-full font-thin text-[15px] py-0 bg-transparent outline-none text-custom-100 tracking-normal group-hover:border-b focus:border-b focus:caret-orange border-custom-100"
      />
    </div>
  </div>
</template>

<script setup>
import iconDocument from './icons/IconDocument.vue'

defineProps({
  modelValue: {
    default: 'Untitled Document.md',
  },
})
</script>
