<script setup>
import { nextTick, onMounted, onUnmounted, ref, watch } from "vue";

const links = [
  { id: "home", label: "Accueil" },
  { id: "services", label: "Services" },
  { id: "portfolio", label: "Portfolio" },
  { id: "contact", label: "Contact" },
];

const socials = [
  { href: "https://web.whatsapp.com/send?phone=262692471345", label: "WhatsApp : +262 692 47 13 45", icon: "phone" },
  { href: "mailto:nicarap@hotmail.com", label: "Email : nicarap@hotmail.com", icon: "envelope" },
  { href: "https://www.linkedin.com/in/raphael-lebon-81606918b", label: "LinkedIn", icon: ["fab", "linkedin-in"] },
];

const active = ref("home");
const open = ref(false);

let observer;

const goTo = async (id) => {
  open.value = false;
  await nextTick();
  document.getElementById(id)?.scrollIntoView({ behavior: "smooth" });
  history.replaceState(null, "", `#${id}`);
};

const onKeydown = (e) => {
  if (e.key === "Escape") open.value = false;
};

watch(open, (value) => {
  document.body.style.overflow = value ? "hidden" : "";
});

onMounted(() => {
  window.addEventListener("keydown", onKeydown);

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) active.value = entry.target.id;
      });
    },
    { rootMargin: "-45% 0px -50% 0px" }
  );

  links.forEach(({ id }) => {
    const section = document.getElementById(id);
    if (section) observer.observe(section);
  });
});

onUnmounted(() => {
  window.removeEventListener("keydown", onKeydown);
  observer?.disconnect();
  document.body.style.overflow = "";
});
</script>

<template>
  <header>
    <nav
      class="fixed inset-x-0 top-0 z-50 bg-primary-950 py-3 shadow-lg shadow-black/10"
      aria-label="Navigation principale"
    >
      <div class="mx-auto flex max-w-7xl items-center justify-between px-4 sm:px-6 lg:px-8">
        <a href="#home" class="font-display text-2xl font-semibold tracking-widest text-white" aria-label="Raphaël LEBON — accueil">
          <span class="text-secondary">R</span>L
        </a>

        <div class="hidden items-center gap-8 lg:flex">
          <ul class="flex items-center gap-1">
            <li v-for="link in links" :key="link.id">
              <a
                :href="`#${link.id}`"
                class="group relative px-3 py-2 text-sm font-medium uppercase tracking-[0.15em] transition-colors"
                :class="active === link.id ? 'text-secondary' : 'text-primary-100 hover:text-white'"
                :aria-current="active === link.id ? 'page' : undefined"
              >
                {{ link.label }}
                <span
                  class="absolute inset-x-3 -bottom-0.5 h-px origin-left bg-secondary transition-transform duration-300"
                  :class="active === link.id ? 'scale-x-100' : 'scale-x-0 group-hover:scale-x-100'"
                ></span>
              </a>
            </li>
          </ul>

          <span class="h-6 w-px bg-white/20" aria-hidden="true"></span>

          <div class="flex items-center gap-1">
            <a
              v-for="social in socials"
              :key="social.href"
              :href="social.href"
              target="_blank"
              rel="noopener"
              :title="social.label"
              :aria-label="social.label"
              class="flex h-9 w-9 items-center justify-center rounded-full text-primary-100 transition hover:bg-white/10 hover:text-secondary"
            >
              <fa :icon="social.icon" />
            </a>
          </div>
        </div>

        <button
          type="button"
          class="relative flex h-10 w-10 items-center justify-center rounded-full text-white transition hover:bg-white/10 lg:hidden"
          :aria-label="open ? 'Fermer le menu' : 'Ouvrir le menu'"
          :aria-expanded="open"
          aria-controls="mobile-menu"
          @click="open = !open"
        >
          <span class="sr-only">Menu</span>
          <span class="absolute h-0.5 w-6 bg-current transition duration-300" :class="open ? 'rotate-45' : '-translate-y-2'"></span>
          <span class="absolute h-0.5 w-6 bg-current transition duration-300" :class="open ? 'opacity-0' : ''"></span>
          <span class="absolute h-0.5 w-6 bg-current transition duration-300" :class="open ? '-rotate-45' : 'translate-y-2'"></span>
        </button>
      </div>
    </nav>

    <!-- Menu mobile (hors du <nav> : backdrop-blur créerait un contexte pour position: fixed) -->
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0"
      leave-active-class="transition duration-200 ease-in"
      leave-to-class="opacity-0"
    >
      <div
        v-if="open"
        id="mobile-menu"
        class="fixed inset-0 z-40 flex flex-col bg-primary-950 px-6 pb-10 pt-24 lg:hidden"
      >
        <ul class="flex flex-col gap-2">
          <li v-for="(link, i) in links" :key="link.id">
            <a
              :href="`#${link.id}`"
              class="flex items-baseline gap-4 border-b border-white/10 py-4 font-display text-3xl tracking-wide transition-colors"
              :class="active === link.id ? 'text-secondary' : 'text-white hover:text-secondary'"
              @click.prevent="goTo(link.id)"
            >
              <span class="font-sans text-xs text-primary-300">0{{ i + 1 }}</span>
              {{ link.label }}
            </a>
          </li>
        </ul>
        <div class="mt-auto flex gap-3">
          <a
            v-for="social in socials"
            :key="social.href"
            :href="social.href"
            target="_blank"
            rel="noopener"
            :aria-label="social.label"
            class="flex h-12 w-12 items-center justify-center rounded-full border border-white/15 text-secondary transition hover:border-secondary"
          >
            <fa :icon="social.icon" />
          </a>
        </div>
      </div>
    </Transition>
  </header>
</template>
