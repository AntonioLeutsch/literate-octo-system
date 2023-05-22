<!--
  This example requires some changes to your config:
  
  ```
  // tailwind.config.js
  module.exports = {
    // ...
    plugins: [
      // ...
      require('@tailwindcss/forms'),
    ],
  }
  ```
-->
<template>
  <footer class="bg-gray-900" aria-labelledby="footer-heading">
    <h2 id="footer-heading" class="sr-only">Footer</h2>
    <div class="mx-auto max-w-7xl px-6 pb-8 pt-20 sm:pt-24 lg:px-8 lg:pt-32">
      <div class="xl:grid xl:grid-cols-2 xl:gap-8">
        <div class="md:grid md:grid-cols-2 md:gap-8">
          <div>
            <h3 class="text-sm font-semibold leading-6 text-white">Service</h3>
            <ul role="list" class="mt-6 space-y-4">
              <li v-for="item in navigation.service" :key="item.name">
                <a
                  :href="item.href"
                  class="text-sm leading-6 text-gray-300 hover:text-white"
                  >{{ item.name }}</a
                >
              </li>
            </ul>
          </div>
          <div class="mt-10 md:mt-0">
            <h3 class="text-sm font-semibold leading-6 text-white">
              Rechtliches
            </h3>
            <ul role="list" class="mt-6 space-y-4">
              <li v-for="item in navigation.legal" :key="item.name">
                <a
                  :href="item.href"
                  class="text-sm leading-6 text-gray-300 hover:text-white"
                  >{{ item.name }}</a
                >
              </li>
            </ul>
          </div>
        </div>
        <div class="mt-10 xl:mt-0">
          <h3 class="text-sm font-semibold leading-6 text-white">InfoMails</h3>
          <p class="mt-2 text-sm text-gray-300">
            <strong
              >Die Newsletter enthalten Informationen über uns sowie Einladungen
              zu unseren Veranstaltungen.</strong
            >
          </p>
          <form
            class="mt-4 sm:flex sm:max-w-md"
            @submit.prevent="stupidNewsletterForm"
          >
            <label for="email-address" class="sr-only">Email address</label>
            <input
              type="email"
              name="email-address"
              id="email-address"
              autocomplete="email"
              required
              class="w-full min-w-0 appearance-none rounded-md border-0 bg-white/25 px-3 py-1.5 text-base text-white shadow-sm ring-1 ring-inset ring-white/10 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-emerald-500 sm:w-64 sm:text-sm sm:leading-6 xl:w-full"
              placeholder="E-Mail Adresse"
              v-model="email"
            />
            <div class="mt-4 sm:ml-4 sm:mt-0 sm:flex-shrink-0">
              <button
                type="submit"
                class="flex w-full items-center justify-center rounded-md bg-emerald-500 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-emerald-400 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-emerald-500"
              >
                Jetzt eintragen
              </button>
            </div>
          </form>
          <p class="mt-2 text-xs opacity-75 text-gray-300">
            Hinweise zum Anmeldeverfahren, Versanddienstleister, statistischer
            Auswertung und Widerruf in unserer Datenschutzerklärung.
          </p>
        </div>
      </div>
      <div class="mt-16 border-t border-white/10 pt-8 sm:mt-20 lg:mt-24">
        <p class="mt-8 text-xs leading-5 text-gray-400 text-center md:mt-0">
          Copyright © 2023 Hinweis: Links auf externe Seiten sind sog.
          Affiliate-Links durch die eine
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
import { ref } from "vue";
import type { Ref } from "vue";

interface NavigationItem {
  name: string;
  href: string;
}

interface Navigation {
  service: NavigationItem[];
  legal: NavigationItem[];
}

const navigation: Navigation = {
  service: [
    { name: "Über Uns", href: "#" },
    { name: "Presse", href: "#" },
    { name: "Sponsoring", href: "#" },
    { name: "Barcamp", href: "#" },
  ],
  legal: [
    { name: "Kontakt", href: "#" },
    { name: "Impressum", href: "#" },
    { name: "Datenschutzerklärung", href: "#" },
  ],
};

const email: Ref<string> = ref("");

const stupidNewsletterForm = () => {
  // submit form to backend using fetch

  // send to endpoint /api/newsletter
  fetch("/api/newsletter", {
    method: "POST",
    body: JSON.stringify({ email: email.value }),
  });

  // reset form
  email.value = "";

  // show success message
  alert("Erfolgreich eingetragen");
};
</script>
