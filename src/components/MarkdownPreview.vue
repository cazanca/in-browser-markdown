<template>
  <section class="min-h-full bg-custom-100 dark:bg-custom-1000" :class="[isPreviewMdOpen ? ' grid' :'md:grid md:grid-cols-2 justify-center']">

    <article :class="[isPreviewMdOpen ? 'md:hidden' : 'md:block border-r border-custom-300 dark:border-custom-800', {'hidden': isPreviewOpen}]">
      
      <MarkdownHeader title="markdown">
        
        <button type="button" @click.prevent="isPreviewOpen = true" class="md:hidden">
          <IconShowPreview />
        </button>
      </MarkdownHeader>
      <div class="h-screen md:h-full px-5 py-4 md:py-5">

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
      
      <div v-html="convertHTML" id="preview" class="h-full px-5 py-4 font-mono text-custom-700 dark:text-custom-400 md:py-5" :class="isPreviewMdOpen ? 'md:w-[800px] md:mx-auto': ''">
        
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
<style>
#preview {
  @apply text-custom-500 dark:text-custom-400 space-y-5;
}

#preview h1 {
  @apply font-bold text-3xl text-custom-700 dark:text-custom-100;
}

#preview h2,
#preview h3,
#preview h4,
#preview h5 {
  @apply font-serif;
}

#preview h2 {
  @apply font-light text-2xl text-custom-700 dark:text-custom-100;
}

#preview h3,
#preview h4,
#preview h5 {
  @apply font-bold text-custom-700 dark:text-custom-100;
}

#preview h3 {
  @apply text-xl;
}

#preview h4 {
  @apply text-lg;
}

#preview h5 {
  @apply text-custom-700;
}

#preview h6 {
  @apply font-serif font-bold text-sm text-orange;
}

#preview p {
  @apply text-sm;
}

#preview ol,
#preview ul {
  @apply font-serif text-sm ml-6;
}

#preview ol {
  @apply list-decimal;
}

#preview ol li {
  @apply ml-2 pl-2; /* Adjusted left margin and padding */
}

#preview ul {
  @apply list-none;
}

#preview ul li {
  @apply relative pl-5; /* Updated padding */
}

#preview ul li::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0.5em; /* Adjust vertical alignment */
  width: 0.4em; /* Bullet size */
  height: 0.4em; /* Bullet size */
  border-radius: 50%;
  @apply bg-orange;
}

#preview blockquote {
  @apply bg-custom-200 dark:bg-custom-800 border-l-4 border-orange p-6 text-sm font-serif font-bold rounded text-custom-1000 dark:text-custom-100;
}

#preview blockquote a {
  @apply underline;
}

#preview code {
  @apply text-sm font-mono text-custom-700 dark:text-custom-100;
}

#preview pre {
  @apply bg-custom-200 text-custom-700 rounded p-3 md:p-6 text-[11px] md:text-sm font-mono dark:bg-custom-800 dark:text-custom-100;
}
</style>
