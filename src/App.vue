<script setup lang="ts">
import { onMounted, ref } from "vue";

import Footer from "./components/Footer.vue";

const app = ref<HTMLElement | null>(null);

/**
 * Function that catches clicks on hyperlinks without a href attribute or with a href attribute that starts with #.
 * Then it throws an error to Sentry.
 * @param {MouseEvent} event
 * @returns {void}
 */
const watchForAnchorClicks = (event: MouseEvent): void => {
  if (event.target instanceof HTMLAnchorElement) {
    const href = event.target.getAttribute("href");
    if (href === null || href.startsWith("#")) {
      event.preventDefault();
      throw new Error("Anchor without href clicked");
    }
  }
};

onMounted(() => {
  app.value?.addEventListener("click", watchForAnchorClicks);
});
</script>

<template>
  <div ref="app">
    <router-view />
    <Footer />
  </div>
</template>
