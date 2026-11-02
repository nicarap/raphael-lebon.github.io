<script setup>
const projects = [
  {
    title: "Travel Planner by Coco",
    description:
      "Site vitrine d'une organisatrice de voyages sur mesure : présentation des offres, identité visuelle soignée et parcours pensé pour convertir les visiteurs en clients.",
    image: `${import.meta.env.BASE_URL}images/projects/travelplanner.png`,
    url: "https://www.travelplannerbycoco.fr",
    domain: "travelplannerbycoco.fr",
    tags: ["UI/UX Design", "Développement web", "Responsive"],
  },
];
</script>

<template>
  <section id="portfolio" class="relative w-full overflow-hidden bg-primary-950 py-24 sm:py-32">
    <div class="pointer-events-none absolute -right-40 -top-40 h-96 w-96 rounded-full bg-primary-700/30 blur-3xl" aria-hidden="true"></div>

    <div class="relative mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <span class="section-eyebrow">Réalisations</span>
        <h2 class="section-title text-white">Portfolio</h2>
        <p class="mt-5 text-lg leading-relaxed text-primary-200">
          Une sélection de projets conçus et développés pour mes clients.
        </p>
      </div>

      <div class="mt-16 grid gap-8 lg:grid-cols-3">
        <article
          v-for="project in projects"
          :key="project.title"
          class="group overflow-hidden rounded-2xl bg-primary-900/60 ring-1 ring-white/10 transition duration-300 hover:ring-secondary/50 lg:col-span-2"
        >
          <a :href="project.url" target="_blank" rel="noopener" class="block overflow-hidden" :aria-label="`Voir le site ${project.title}`">
            <img
              :src="project.image"
              :alt="`Aperçu du site ${project.title}`"
              class="aspect-[16/10] w-full object-cover object-top transition duration-700 group-hover:scale-105"
              loading="lazy"
            />
          </a>
          <div class="p-6 sm:p-8">
            <ul class="flex flex-wrap gap-2">
              <li
                v-for="tag in project.tags"
                :key="tag"
                class="rounded-full bg-secondary/10 px-3 py-1 text-xs font-medium text-secondary"
              >
                {{ tag }}
              </li>
            </ul>
            <h3 class="mt-4 font-display text-2xl font-medium tracking-wide text-white">{{ project.title }}</h3>
            <p class="mt-3 leading-relaxed text-primary-200">{{ project.description }}</p>
            <a
              :href="project.url"
              target="_blank"
              rel="noopener"
              class="mt-6 inline-flex items-center gap-2 text-sm font-semibold text-secondary transition hover:gap-3"
            >
              {{ project.domain }}
              <fa icon="arrow-up-right-from-square" class="h-3 w-3" />
            </a>
          </div>
        </article>

        <a
          href="#contact"
          class="group flex flex-col justify-between rounded-2xl border border-dashed border-secondary/40 p-8 transition duration-300 hover:border-secondary hover:bg-white/[0.03]"
        >
          <div>
            <span class="section-eyebrow">Bientôt</span>
            <h3 class="mt-4 font-display text-2xl font-medium tracking-wide text-white">
              Nouveaux projets en préparation
            </h3>
            <p class="mt-3 leading-relaxed text-primary-200">
              D'autres réalisations arrivent prochainement. Et si la prochaine était la vôtre ?
            </p>
          </div>
          <span class="mt-10 inline-flex items-center gap-2 text-sm font-semibold text-secondary transition group-hover:gap-3">
            Discutons de votre projet
            <fa icon="arrow-right" />
          </span>
        </a>
      </div>
    </div>
  </section>
</template>
