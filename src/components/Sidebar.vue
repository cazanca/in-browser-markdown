<template>
  <aside
    class="min-h-screen flex flex-col justify-between bg-custom-900 min-w-[250px] -ml-[250px] px-6 pt-7 h-full transition-all duration-300 ease-in-out"
    :class="{ 'ml-0': isNavigationOpen }"
  >
    <div class="min-h-[80%] overflow-auto">
      <p class="uppercase text-custom-100 tracking-[5px] font-logo lg:hidden">markdown</p>

      <div class="w-full mt-7 lg:mt-0">
        <p class="uppercase text-custom-500 tracking-widest">my documents</p>
        <JButton class="mt-7 w-full">+ new document</JButton>
        
        <ul class="mt-6 space-y-6 ml-0">
          <li class="min-h-[36px] flex items-center gap-x-[11px]">
            <iconDocument class="text-custom-100" />
            <div class="max-h-[38px] group">
              <p
                class="text-custom-500 font-thin text-[13px] group-hover:text-custom-500"
              >
                01 April 2022
              </p>
              <p
                class="w-full font-thin text-[15px] py-0 bg-transparent outline-none text-custom-100 tracking-normal"
              >
                untitled-document.md
              </p>
            </div>
          </li>
        </ul>

      </div>
    </div>
    <Switch v-model="isDark" />
  </aside>
</template>

<script setup>
import { inject } from 'vue'
import iconDocument from './icons/IconDocument.vue'
import JButton from './JButton.vue'
import Switch from './Switch.vue'

const isDark = inject('isDark')

defineProps({
  isNavigationOpen: {
    type: Boolean,
    required: true,
  },
})
</script>

<style>
.font-logo {
  font-family: 'Commissioner';
}
</style>
