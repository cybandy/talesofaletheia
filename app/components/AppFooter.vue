<script setup lang="ts">
import type { FooterColumn } from '@nuxt/ui'

const columns: FooterColumn[] = [
  {
    label: 'Menu',
    children: [
      {
        label: 'Home',
        to: '/'
      },
      {
        label: 'About',
        to: '#'
      },
      {
        label: 'Stories',
        to: '#'
      },
      {
        label: 'Contact Us',
        to: '#'
      }
    ]
  },
  {
    label: 'Resources',
    children: [
      {
        label: 'F.A.Q',
        to: '#'
      },
      {
        label: 'Support',
        to: '#'
      },
      {
        label: 'Privacy Policy',
        to: '#'
      },
      {
        label: 'Terms of Service',
        to: '#'
      }
    ]
  }
]

const toast = useToast()

const email = ref('')
const loading = ref(false)

function onSubmit() {
  loading.value = true

  toast.add({
    title: 'Subscribed!',
    description: 'You\'ve been subscribed to our newsletter.'
  })
}
</script>

<template>
  <USeparator
    icon="i-qb-qbtech"
    class="h-px"
  />

  <UFooter :ui="{ top: 'border-b border-default' }">
    <template #top>
      <UContainer>
        <UFooterColumns
          :columns="columns"
          :ui="{
            root: 'grid sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4',
            left: 'sm:mb-0 sm:mt-10 lg:mt-0',
            center: 'order-0 sm:order-first lg:order-0 col-span-full lg:col-span-1 grid grid-cols-2',
            right: ' lg:mt-0'
          }"
        >
          <template #left>
            <div class="space-y-2">
              <AppLogo class="shrink-0 w-47 h-14" />
              <div class="space-y-0.5">
                <p class="text-dimmed text-sm">
                  True Inspiring Stories of life
                </p>
              </div>
            </div>
          </template>
          <template #right>
            <form @submit.prevent="onSubmit">
              <UFormField
                name="email"
                label="Subscribe to our newsletter"
                size="lg"
              >
                <template #help>
                  <span>By subscribing to our newsletter you agree to our <u-link
                    to="#"
                    class="text-primary"
                  >privacy policy</u-link></span>
                </template>
                <UInput
                  v-model="email"
                  type="email"
                  class="w-full"
                  placeholder="Enter your email"
                >
                  <template #trailing>
                    <UButton
                      type="submit"
                      size="xs"
                      color="neutral"
                      label="Subscribe"
                    />
                  </template>
                </UInput>
              </UFormField>
            </form>
          </template>
        </UFooterColumns>
      </UContainer>
    </template>

    <template #left>
      <p class="text-muted text-sm">
        QB Tech
      </p>
    </template>

    <p class="text-muted text-sm">
      All rights reserved • Copyright • © {{ new Date().getFullYear() }}
    </p>

    <template #right>
      <UColorModeButton />
      <UButton
        to="https://qbtech.dev"
        target="_blank"
        icon="i-qb-qbtech"
        aria-label="Website"
        color="neutral"
        variant="ghost"
      />
      <UButton
        to="mailto:info@qbtech.dev"
        target="_blank"
        icon="i-lucide-mail"
        aria-label="Send email"
        color="neutral"
        variant="ghost"
      />
      <UButton
        to="https://www.facebook.com/profile.php?id=100083577977374"
        target="_blank"
        icon="i-simple-icons-facebook"
        aria-label="QB Tech on facebook"
        color="neutral"
        variant="ghost"
      />
      <UButton
        to="https://github.com/qb-technology"
        target="_blank"
        icon="i-simple-icons-github"
        aria-label="QB Tech on Github"
        color="neutral"
        variant="ghost"
      />
    </template>
  </UFooter>
</template>
