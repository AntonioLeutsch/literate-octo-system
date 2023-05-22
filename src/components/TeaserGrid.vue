<template>
  <section class="py-24 sm:py-32 mx-auto max-w-7xl px-6 lg:px-8">
    <div
      class="mx-auto mt-16 grid max-w-2xl grid-cols-1 gap-x-8 gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-3"
    >
      <article
        v-for="post in posts"
        :key="post.id"
        class="flex flex-col items-start justify-between"
      >
        <div class="relative w-full">
          <img
            :src="post.imageUrl"
            :alt="post.title"
            class="w-full rounded-2xl bg-zinc-100 object-cover aspect-[16/8]"
          />
          <div
            class="absolute inset-0 rounded-2xl ring-1 ring-inset ring-zinc-900/10"
          />
        </div>
        <div class="max-w-xl">
          <div class="group relative">
            <h3
              class="mt-6 text-xl font-semibold leading-6 text-zinc-900 group-hover:text-zinc-600"
            >
              <a :href="post.href">
                <span class="absolute inset-0" />
                {{ post.title }}
              </a>
            </h3>
            <p class="mt-5 line-clamp-3 text-sm leading-6 text-zinc-600">
              {{ post.description }}
            </p>
          </div>
        </div>
        <div class="mt-6 flex border-t border-zinc-100 pt-6">
          <a
            href="#"
            class="text-sm font-semibold leading-6 text-emerald-600 hover:text-emerald-500"
            >{{ post.linkText }} <span aria-hidden="true">&rarr;</span></a
          >
        </div>
      </article>
    </div>
  </section>
</template>

<script setup lang="ts">
interface Post {
  id: number;
  title: string;
  href: string;
  description: string;
  imageUrl: string;
  linkText: string;
}

const posts: Post[] = [
  {
    id: 1,
    title: "Events",
    href: "#",
    description:
      "Hier findet ihr eine Liste verschiedener Stammtische/ User-Groups in Mitteldeutschland, die für webaffine Menschen sicher interessant sein dürfte.",
    imageUrl:
      "https://webwirtschaft.net/wp-content/uploads/wordpress-meetup-halle-768x401.png",
    linkText: "Zur Event-Übersicht",
  },
  {
    id: 1,
    title: "Jobs",
    href: "#",
    description:
      "Aktuelle Jobangebote aus der IT-Wirtschaft in Mitteldeutschland. das Inserat ist kostenlos es geht schnell und einfach.",
    imageUrl:
      "https://webwirtschaft.net/wp-content/uploads/jobs-it-wirtschaft.jpg",
    linkText: "Zu den Jobangeboten",
  },
  {
    id: 1,
    title: "Blog",
    href: "#",
    description:
      "Hier findet ihr u.a. die [Nachlese] zum letzten Webmontag. Zusätzlich kommentieren wir in Artikeln Themen, die uns wichtig sind. Mach mit!",
    imageUrl:
      "https://webwirtschaft.net/wp-content/uploads/wordpress-multisite-642x300.jpg",
    linkText: "Zu den Blog-Artikeln",
  },
  // More posts...
];
</script>
