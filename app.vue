<template>
  <NuxtLoadingIndicator/>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>

<script setup>
</script>

<script>
export default {
  head() {
    return {
      link: [
        { rel: 'dns-prefetch', href: 'https://fonts.gstatic.com', crossorigin: true },
        { rel: 'preload', href: '/assets/fonts/MonaSans.woff2', as: 'font', type: 'font/woff2', crossorigin: true },
        // Add more fonts as needed
      ],
      title: 'Continuum Glow',
    }
  }
}
</script>




<style>
:root {
  background: #FAFAFA; 
}

.dark {
  background: #09090B; 
}

body {
  overflow-x: hidden;
}

/* Page transition styles */
.page-enter-active, .page-leave-active {
  transition: all 0.2s;
  z-index: 999;
}
.page-enter-from, .page-leave-to {
  opacity: 0;
  z-index: 999;
  filter: blur(0.9rem);
}
</style>
