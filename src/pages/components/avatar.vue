<script setup lang="ts">
import { useHead } from '@vueuse/head'

import { ref } from 'vue'
import useMarkdownToc from '/@src/composable/useMarkdownToc'
import { pageTitle } from '/@src/state/sidebarLayoutState'

const markdownContainer = ref<HTMLElement>()
const toc = useMarkdownToc(markdownContainer)

pageTitle.value = 'VAvatar'
useHead({
  title: 'VAvatar - Components - Vuero',
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
          label: 'VAvatar',
          to: { name: 'components-avatar' },
        },
      ]"
    />

    <div class="columns">
      <div
        ref="markdownContainer"
        :class="[toc.length > 0 ? 'is-9' : 'is-12']"
        class="column doc-column"
      >
        <!--Avatar-->
        <AvatarDefaultDocumentation />

        <!--Avatar Square-->
        <AvatarSquareDocumentation />

        <!--Avatar Fallback-->
        <AvatarHandleFallbackDocumentation />

        <!--Avatar Dot-->
        <AvatarDotDocumentation />

        <!--Avatar Dot Squared-->
        <AvatarDotSquaredDocumentation />

        <!--Avatar Dot Colors-->
        <AvatarDotColorsDocumentation />

        <!--Avatar Badge-->
        <AvatarBadgeDocumentation />

        <!--Avatar Fake-->
        <AvatarFakeDocumentation />

        <!--Avatar Fake Squared-->
        <AvatarFakeSquareDocumentation />

        <!--Avatar Fake Badge-->
        <AvatarFakeBadgeDocumentation />

        <!--Avatar Fake Colors-->
        <AvatarFakeColorDocumentation />

        <!--Avatar Fake Squared Colors-->
        <AvatarFakeSquaredColorDocumentation />

        <!--Props-->
        <AvatarPropsDocumentation />

        <!--Slots-->
        <AvatarSlotsDocumentation />
      </div>
      <div v-if="toc.length" class="column is-3 toc-column">
        <DocumentationToc :toc="toc" />
      </div>
    </div>
  </div>
</template>
