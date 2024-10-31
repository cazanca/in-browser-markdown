<template>
  <section class="h-full bg-custom-100 dark:bg-custom-1000" :class="[isPreviewMdOpen ? 'bg-red-900 grid' :'md:grid md:grid-cols-2 justify-center']">

    <article :class="[isPreviewMdOpen ? 'md:hidden' : 'md:block border-r border-custom-300 dark:border-custom-800', {'hidden': isPreviewOpen}]">
      
      <MarkdownHeader title="markdown">
        
        <button type="button" @click.prevent="isPreviewOpen = true" class="md:hidden">
          <IconShowPreview />
        </button>
      </MarkdownHeader>
      <div class="h-full px-5 py-4 md:py-5">

        <form action="" class="h-full">
          <textarea v-model="markdownText" name="editor" id="editor" class="resize-none w-full h-full outline-none bg-transparent text-custom-700 font-mono text-sm dark:text-custom-400"></textarea>
        </form>
      </div>
    </article>
    
    <article :class="['w-full md:block', {'hidden': !isPreviewOpen}]">
    
      <MarkdownHeader title="preview">
        
        <button type="button" @click.prevent="isPreviewOpen = false" class="md:hidden">
          <IconHidePreview/>
        </button>

        <button type="button" @click.prevent="isPreviewMdOpen = !isPreviewMdOpen" class="hidden md:block">
          <IconShowPreview v-if="!isPreviewMdOpen"/>
          <IconHidePreview v-else/>
        </button>
      </MarkdownHeader>
      
      <div v-html="convertHTML" class="h-full px-5 py-4 font-mono text-custom-700 dark:text-custom-400 md:py-5" :class="isPreviewMdOpen ? 'md:w-[672px] md:mx-auto': ''">
        
      </div>
    </article>
  
  </section>
</template>

<script setup>
import {  computed, ref } from 'vue';
import { marked } from 'marked';

import IconHidePreview from './icons/IconHidePreview.vue';
import IconShowPreview from './icons/IconShowPreview.vue';
import MarkdownHeader from './MarkdownHeader.vue';

const isPreviewOpen = ref(false)
const isPreviewMdOpen = ref(false)

const markdownText = ref('')

const convertHTML = computed(() => {
  return marked.parse(markdownText.value)
})

</script>