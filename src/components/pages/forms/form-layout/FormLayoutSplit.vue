<script setup lang="ts">
import { useWindowScroll } from '@vueuse/core'
import { computed, ref } from 'vue'

const bankAccount = ref('')
const transferFees = ref('')

const { y } = useWindowScroll()

const isStuck = computed(() => {
  return y.value > 30
})
</script>

<template>
  <form class="form-layout is-split" @submit.prevent>
    <div class="form-outer">
      <div :class="[isStuck && 'is-stuck']" class="form-header stuck-header">
        <div class="form-header-inner">
          <div class="left">
            <h3>Request Payout</h3>
          </div>
          <div class="right">
            <div class="buttons">
              <VButton
                icon="lnir lnir-arrow-left rem-100"
                :to="{ name: 'sidebar-layouts-profile-view' }"
                light
                dark-outlined
              >
                Cancel
              </VButton>
              <VButton color="primary" raised> Request Payout </VButton>
            </div>
          </div>
        </div>
      </div>
      <div class="form-body">
        <div class="form-section">
          <div class="left">
            <h3 class="has-text-centered">Choose an amount</h3>
            <div class="operator">
              <span>Or</span>
            </div>
            <VField>
              <VControl>
                <div class="radio-pills">
                  <div class="radio-pill">
                    <input type="radio" name="amount_selection" :value="20" />
                    <div class="radio-pill-inner">
                      <span>$20</span>
                    </div>
                  </div>
                  <div class="radio-pill">
                    <input type="radio" name="amount_selection" :value="40" />
                    <div class="radio-pill-inner">
                      <span>$40</span>
                    </div>
                  </div>
                  <div class="radio-pill">
                    <input type="radio" name="amount_selection" :value="60" />
                    <div class="radio-pill-inner">
                      <span>$60</span>
                    </div>
                  </div>
                  <div class="radio-pill">
                    <input type="radio" name="amount_selection" :value="100" />
                    <div class="radio-pill-inner">
                      <span>$100</span>
                    </div>
                  </div>
                </div>
              </VControl>
            </VField>
          </div>
          <div class="right">
            <h3 class="has-text-centered">Enter your own</h3>
            <VField>
              <VControl icon="feather:dollar-sign">
                <input
                  class="input"
                  type="number"
                  min="0"
                  step="10"
                  placeholder="Amount..."
                />
              </VControl>
            </VField>
          </div>
        </div>
        <div class="form-section is-grey">
          <div class="left">
            <h3>Personal Info</h3>
            <VField>
              <VControl icon="feather:user">
                <input
                  type="text"
                  class="input"
                  placeholder="First Name *"
                  autocomplete="given-name"
                />
              </VControl>
            </VField>
            <VField>
              <VControl icon="feather:user">
                <input
                  type="text"
                  class="input"
                  placeholder="Last Name *"
                  autocomplete="family-name"
                />
              </VControl>
            </VField>
            <VField>
              <VControl icon="feather:mail">
                <input
                  type="email"
                  class="input"
                  placeholder="Email Address *"
                  autocomplete="email"
                  inputmode="email"
                />
              </VControl>
            </VField>
            <VField>
              <VControl icon="feather:phone">
                <input
                  type="tel"
                  class="input"
                  placeholder="Phone Number *"
                  autocomplete="tel"
                  inputmode="tel"
                />
              </VControl>
            </VField>
          </div>
          <div class="right">
            <h3>Payout Details</h3>

            <VField>
              <VControl>
                <Multiselect
                  v-model="bankAccount"
                  placeholder="Bank Account"
                  :options="['AMEX **** 42', 'HSBC **** 29']"
                />
              </VControl>
            </VField>

            <VField>
              <VControl>
                <Multiselect
                  v-model="transferFees"
                  placeholder="Bank Account"
                  :options="['Super Fast - $3.00', 'Regular - $0.50']"
                />
              </VControl>
            </VField>

            <VField>
              <label>Notify me when funds are ready?</label>
              <VControl>
                <label class="radio">
                  <input type="radio" name="notification_selection" checked />
                  <span></span>
                  Yes
                </label>

                <label class="radio is-outlined is-primary">
                  <input type="radio" name="notification_selection" />
                  <span></span>
                  No
                </label>
              </VControl>
            </VField>
          </div>
        </div>
      </div>
    </div>
  </form>
</template>

<style lang="scss">
@import '../../../../scss/abstracts/_mixins.scss';
@import '../../../../scss/pages/generic/_forms.scss';
</style>
