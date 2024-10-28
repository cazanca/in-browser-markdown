<template>
  <!--px-7 bg-custom-800 removed-->
  <div class="inline-flex items-center gap-2 min-h-[72px] py-6">
    <label
      for="switch-component-on"
      class="text-custom-100"
      :class="{ 'text-custom-600': modelValue }"
      ><IconMoon
    /></label>
    <div class="relative inline-block w-11 h-6">
      <input
        type="checkbox"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.checked)"
        id="switch-component-on"
        class="peer appearance-none w-12 h-6 bg-custom-600 rounded-full checked:bg-custom-600 cursor-pointer transition-colors duration-300"
      />
      <label
        for="switch-component-on"
        class="absolute top-1.5 left-1.5 w-3 h-3 bg-white rounded-full shadow-sm transition-transform duration-300 peer-checked:translate-x-6 cursor-pointer"
        :class="{ 'translate-x-6': modelValue }"
      ></label>
    </div>
    <label
      for="switch-component-on"
      class="text-custom-100"
      :class="{ 'text-custom-600': !modelValue }"
      ><IconSun
    /></label>
  </div>
</template>

<script setup>
import IconMoon from './icons/IconMoon.vue'
import IconSun from './icons/IconSun.vue'

defineProps({
  modelValue: {
    required: true,
    type: Boolean,
  },
})
</script>
