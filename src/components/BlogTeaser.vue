<template>
  <div class="bg-white py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <h2 class="text-3xl font-bold tracking-tight text-zinc-900 sm:text-4xl">
          Aus dem Blog
        </h2>
        <p class="mt-2 text-lg leading-8 text-zinc-600">
          Hier findet ihr u.a. die Nachlese zum letzten Webmontag. Zusätzlich
          kommentieren wir in Artikeln Themen, die uns wichtig sind. Mach mit!
        </p>
      </div>
      <div
        class="mx-auto mt-16 grid max-w-2xl grid-cols-1 gap-x-8 gap-y-20 lg:mx-0 lg:max-w-none lg:grid-cols-3"
      >
        <article
          v-for="post in posts"
          :key="post.id"
          class="flex flex-col items-start justify-start"
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
            <div class="mt-8 flex items-center gap-x-4 text-xs">
              <time :datetime="post.datetime" class="text-zinc-500">{{
                post.date
              }}</time>
            </div>
            <div class="group relative">
              <h3
                class="mt-3 text-lg font-semibold leading-6 text-zinc-900 group-hover:text-zinc-600"
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
        </article>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Post {
  id: number;
  title: string;
  href: string;
  description: string;
  imageUrl: string;
  date: string;
  datetime: string;
}

const posts: Post[] = [
  {
    id: 1,
    title: "Die meistbesuchten Webseiten aus Sachsen-Anhalt",
    href: "#",
    description:
      "Welche sind die meistbesuchtesten Webseiten aus Sachsen-Anhalt? Mehr als die Hälfte der Top50 wurden in Halle entwickelt, ein Viertel in Magdeburg.",
    imageUrl:
      "https://webwirtschaft.net/wp-content/uploads/top-webseiten-sachsen-anhalt.png",
    date: "18.01.2023",
    datetime: "2023-01-18",
  },
  {
    id: 2,
    title: "Das sind die Top Startups aus Sachsen-Anhalt 2022",
    href: "#",
    description:
      "Wer sind die bekanntesten Startups und Technologieunternehmen in Sachsen-Anhalt? Ranking der 75 innovativsten Tech-Firmen zwischen Magdeburg und Halle.",
    imageUrl:
      "https://webwirtschaft.net/wp-content/uploads/startups-in-sachsen-anhalt.png",
    date: "18.01.2023",
    datetime: "2023-01-18",
  },
  {
    id: 3,
    title: "Sommer-Termine für Gründer und Startups",
    href: "#",
    description:
      "So viele Startup Veranstaltungen gab es noch nie, denn Netzwerkveranstaltungen für Gründer sind im Trend.",
    imageUrl:
      "https://webwirtschaft.net/wp-content/uploads/genehmigtes-tgz-foto.jpg",
    date: "18.01.2023",
    datetime: "2023-01-18",
  },
  // More posts...
];
</script>
