<script setup>
const services = [
  {
    icon: "wand-magic-sparkles",
    title: "UI/UX Design",
    text: "De la conceptualisation à la réalisation, je vous accompagne dans la création d'interfaces esthétiques et fonctionnelles, conçues pour offrir une expérience utilisateur exceptionnelle.",
  },
  {
    icon: "code",
    title: "Développement d'applications web",
    text: "Que vous cherchiez à optimiser vos processus internes, à améliorer l'engagement client ou à lancer une plateforme innovante, je transforme vos idées en solutions numériques performantes et sécurisées.",
  },
  {
    icon: "thumbs-up",
    title: "Community management",
    text: "Je vous aide à développer votre présence en ligne à travers des stratégies de communication authentiques et personnalisées.",
  },
  {
    icon: "file-invoice",
    title: "Gestion de projets",
    text: "Je vous accompagne dans l'analyse de vos besoins et dans la rédaction de cahiers des charges fonctionnels et techniques.",
  },
];
</script>

<template>
  <section id="services" class="relative w-full bg-primary-100 py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <span class="section-eyebrow !text-primary-600">Ce que je propose</span>
        <h2 class="section-title text-primary-950">Services</h2>
        <p class="mt-5 text-lg leading-relaxed text-primary-900">
          Quelle que soit votre problématique, nous travaillerons ensemble à trouver des
          solutions innovantes pour répondre à vos besoins.
        </p>
      </div>

      <div class="mt-16 grid gap-6 sm:grid-cols-2 xl:grid-cols-4">
        <article
          v-for="(service, i) in services"
          :key="service.title"
          class="group relative flex flex-col overflow-hidden rounded-2xl border-t-4 border-secondary bg-white p-8 shadow-lg shadow-primary-900/10 transition duration-300 hover:-translate-y-1 hover:shadow-xl hover:shadow-primary-900/20"
        >
          <span class="absolute right-6 top-5 font-display text-4xl font-semibold text-primary-100">0{{ i + 1 }}</span>
          <div class="relative flex h-16 w-16 items-center justify-center rounded-xl bg-primary-950 text-secondary shadow-md">
            <fa :icon="service.icon" class="h-7 w-7" />
          </div>
          <h3 class="mt-6 font-display text-2xl font-medium tracking-wide text-primary-950">
            {{ service.title }}
          </h3>
          <span class="mt-3 h-0.5 w-10 bg-secondary transition-all duration-300 group-hover:w-16" aria-hidden="true"></span>
          <p class="mt-4 leading-relaxed text-gray-700">{{ service.text }}</p>
        </article>
      </div>
    </div>
  </section>
</template>
