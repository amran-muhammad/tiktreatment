<script setup lang="ts">
import { ref } from 'vue'
import { useHead } from '@vueuse/head'

import packageJson from '../../package.json'
import { isDark, toggleDarkModeHandler } from '/@src/state/darkModeState'

type TabId = 'elements' | 'components' | 'forms' | 'plugins'
const activeTab = ref<TabId>('elements')

useHead({
  title: 'Tik Treatment',
})
</script>

<template>
  <MinimalLayout theme="light">
    <div class="landing-page-wrapper">
      <!-- Hero and Navbar -->
      <div id="vuero-landing" class="hero is-fullheight rounded-hero is-active">
        <!-- Navbar partial -->
        <LandingNavigation />

        <div class="absolute-header">
          <div class="header-inner">
            <img
              class="cut-circle light-image-l"
              src="/@src/assets/shapes/cut-circle.svg"
              alt=""
            />
            <img
              class="cut-circle dark-image-l"
              src="/@src/assets/shapes/cut-circle-dark.svg"
              alt=""
            />
          </div>
        </div>

        <div class="hero-body has-text-centered">
          <div class="container">
            <div class="switch-wrapper">
              <div class="night-toggle night-toggle--daynight">
                <input
                  id="night-toggle--daynight"
                  type="checkbox"
                  class="night-toggle--checkbox"
                  :checked="!isDark"
                  aria-label="Toggle dark mode"
                  @change="toggleDarkModeHandler"
                />
                <label class="night-toggle--btn" for="night-toggle--daynight">
                  <span class="night-toggle--feature"></span>
                </label>
              </div>
            </div>

            <img
              class="header_img"
              src="/@src/assets/home/undraw_product_explainer_8jbm.svg"
              alt="Don't let emergencies catch you off guard - trust tiktreatment.com to have your back!"
            />

            <h1 class="title is-1 is-bold is-light">
              Quick aid just a click away with
              <span>TikTreatment</span>!
            </h1>
            <h3 class="subtitle is-4 is-light">
              Be prepared for the unexpected with TikTreatment - your one-stop
              first aid solution!
            </h3>
          </div>
        </div>
      </div>
      <div class="container p-b-20 podcast">
        <TilesGridV3 />
      </div>

      <!-- Footer -->
      <LandingFooter />

      <!-- Back To Top Button -->
      <div id="backtotop">
        <a href="#" aria-label="back to top">
          <i aria-hidden="true" class="fas fa-angle-up"></i>
        </a>
      </div>
    </div>
  </MinimalLayout>
</template>

<style lang="scss">
@import '../scss/abstracts/_mixins.scss';
@import '../scss/pages/demo/_landing.scss';
.landing-page-wrapper .hero.rounded-hero .hero-body .title span {
  color: #f50057;
}
@media only screen and (max-width: 767px) {
  /* CSS rules for mobile devices */
  .podcast {
    padding-top: 310px !important;
    padding: 5%;
  }
}
</style>
