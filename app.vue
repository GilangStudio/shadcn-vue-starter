<template>
  <div class="mobile-container">
    <main class="pb-20">
      <NuxtPage />
    </main>
    <BottomNavigation />
  </div>
</template>

<script setup>
// Meta tags untuk mobile
useHead({
  title: 'Mobile App Template',
  meta: [
    { name: 'description', content: 'Template aplikasi mobile dengan Nuxt 3 dan Shadcn UI' }
  ]
})
</script>