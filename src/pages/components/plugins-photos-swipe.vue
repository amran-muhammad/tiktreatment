<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { ref } from 'vue'
import useMarkdownToc from '/@src/composable/useMarkdownToc'
import { pageTitle } from '/@src/state/sidebarLayoutState'

const markdownContainer = ref<HTMLElement>()
const toc = useMarkdownToc(markdownContainer)

pageTitle.value = 'VPhotosSwipe'
useHead({
  title: 'VPhotosSwipe - Plugins - Vuero',
})
</script>

<template>
  <div class="page-content-inner">
    <VBreadcrumb
      with-icons
      separator="bullet"
      :items="[
        {
          label: 'Vuero',
          hideLabel: true,
          icon: 'feather:home',
          to: { name: 'index' },
        },
        {
          label: 'Components',
          to: { name: 'components' },
        },
        {
          label: 'Plugins',
        },
        {
          label: 'VPhotosSwipe',
          to: { name: 'components-plugins-photos-swipe' },
        },
      ]"
    />

    <div class="columns is-multiline">
      <div
        ref="markdownContainer"
        :class="[toc.length > 0 ? 'is-9' : 'is-12']"
        class="column doc-column"
      >
        <!--Thumbnails-->
        <GalleryImagesDocumentation />

        <!--Curved Thumbnails-->
        <GalleryImagesCurvedDocumentation />

        <!--Rounded Thumbnails-->
        <GalleryImagesRoundedDocumentation />

        <!--Bigger Thumbnails-->
        <GalleryImagesLargerDocumentation />
      </div>
      <div v-if="toc.length" class="column is-3 toc-column">
        <DocumentationToc :toc="toc" />
      </div>
    </div>
  </div>
</template>
