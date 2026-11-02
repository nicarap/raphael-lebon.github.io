<script setup>
const year = new Date().getFullYear();

const socials = [
  { href: "https://web.whatsapp.com/send?phone=262692471345", label: "WhatsApp", icon: "phone" },
  { href: "mailto:nicarap@hotmail.com", label: "Email", icon: "envelope" },
  { href: "https://www.linkedin.com/in/raphael-lebon-81606918b", label: "LinkedIn", icon: ["fab", "linkedin-in"] },
];

</script>

<template>
  <footer class="w-full bg-primary-950 text-primary-200">
    <div class="mx-auto flex max-w-7xl flex-col items-center justify-between gap-6 px-4 py-10 sm:flex-row sm:px-6 lg:px-8">
      <a href="#home" class="font-display text-2xl font-semibold tracking-widest text-white" aria-label="Retour à l'accueil">
        <span class="text-secondary">R</span>L
      </a>

      <p class="text-center text-sm">
        © {{ year }} Raphaël LEBON — UI/UX Designer & Développeur Web
      </p>

      <div class="flex gap-2">
        <a
          v-for="social in socials"
          :key="social.href"
          :href="social.href"
          target="_blank"
          rel="noopener"
          :aria-label="social.label"
          class="flex h-9 w-9 items-center justify-center rounded-full ring-1 ring-white/10 transition hover:text-secondary hover:ring-secondary"
        >
          <fa :icon="social.icon" />
        </a>
      </div>
    </div>
      <a
        href="#home"
        aria-label="Retour en haut de la page"
        title="Retour en haut de la page"
        class="fixed bottom-6 right-6 z-30 flex h-12 w-12 items-center justify-center rounded-full bg-secondary text-primary-950 shadow-lg shadow-black/20 transition hover:-translate-y-1"
      >
        <fa icon="arrow-up" />
      </a>
  </footer>
</template>
