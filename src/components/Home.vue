<script setup>
const background = `url('${import.meta.env.BASE_URL}images/header/background.webp')`;
</script>

<template>
  <section
    id="home"
    class="relative isolate flex min-h-[100svh] w-full items-center overflow-hidden bg-primary-950 bg-cover bg-center md:bg-fixed"
    :style="{ backgroundImage: background }"
  >
    <!-- Overlays pour la lisibilité -->
    <div class="absolute inset-0 -z-10 bg-gradient-to-r from-primary-950/95 via-primary-900/80 to-primary-900/40" aria-hidden="true"></div>
    <div class="absolute inset-x-0 bottom-0 -z-10 h-40 bg-gradient-to-t from-primary-950/80 to-transparent" aria-hidden="true"></div>

    <div class="mx-auto w-full max-w-7xl px-4 pb-24 pt-32 sm:px-6 lg:px-8">
      <div class="max-w-3xl">
        <p class="inline-flex items-center gap-2 rounded-full border border-white/15 bg-white/5 px-4 py-1.5 text-xs font-medium uppercase tracking-[0.2em] text-primary-100 backdrop-blur">
          <span class="relative flex h-2 w-2">
            <span class="absolute inline-flex h-full w-full animate-ping rounded-full bg-secondary opacity-75"></span>
            <span class="relative inline-flex h-2 w-2 rounded-full bg-secondary"></span>
          </span>
          Disponible pour vos projets · La Réunion
        </p>

        <h1 class="mt-8 font-display text-6xl font-medium uppercase leading-[0.95] tracking-wide text-white sm:text-8xl">
          <span class="text-secondary">R</span>aphaël<br />
          <span class="text-secondary">L</span>ebon
        </h1>

        <p class="mt-6 font-display text-xl uppercase tracking-[0.2em] text-primary-200 sm:text-2xl">
          UI/UX Designer <span class="text-secondary">&</span> Développeur Web
        </p>

        <p class="mt-6 max-w-xl text-base leading-relaxed text-primary-100/90 sm:text-lg">
          Je conçois et développe des interfaces web élégantes, performantes et pensées
          pour vos utilisateurs — de l'idée jusqu'à la mise en ligne.
        </p>

        <div class="mt-10 flex flex-wrap gap-4">
          <a href="#portfolio" class="btn-gold">
            Voir mes réalisations
            <fa icon="arrow-right" />
          </a>
          <a href="#contact" class="btn-outline">Me contacter</a>
        </div>
      </div>
    </div>

    <a
      href="#services"
      class="absolute bottom-8 left-1/2 flex -translate-x-1/2 flex-col items-center gap-2 text-xs uppercase tracking-[0.3em] text-primary-200 transition hover:text-secondary"
      aria-label="Découvrir mes services"
    >
      <span class="hidden sm:block">Découvrir</span>
      <fa icon="chevron-down" class="animate-bounce-slow" />
    </a>
  </section>
</template>
