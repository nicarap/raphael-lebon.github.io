<script setup>
const channels = [
  {
    icon: "phone",
    label: "Téléphone / WhatsApp",
    value: "+262 692 47 13 45",
    href: "https://web.whatsapp.com/send?phone=262692471345",
  },
  {
    icon: "envelope",
    label: "Email",
    value: "nicarap@hotmail.com",
    href: "mailto:nicarap@hotmail.com",
  },
  {
    icon: ["fab", "linkedin-in"],
    label: "LinkedIn",
    value: "Raphaël LEBON",
    href: "https://www.linkedin.com/in/raphael-lebon-81606918b",
  },
];
</script>

<template>
  <section id="contact" class="w-full bg-primary-50 py-24 sm:py-32">
    <div class="mx-auto grid max-w-7xl items-center gap-12 px-4 sm:px-6 lg:grid-cols-2 lg:gap-20 lg:px-8">
      <div>
        <span class="section-eyebrow">Contact</span>
        <h2 class="section-title text-primary-950">
          Un projet en tête ?<br />Parlons-en autour d'un café.
        </h2>
        <p class="mt-5 max-w-lg text-lg leading-relaxed text-gray-600">
          N'hésitez pas à me contacter pour échanger sur vos besoins. Je vous réponds
          rapidement avec une première proposition adaptée.
        </p>
        <a href="mailto:nicarap@hotmail.com" class="btn mt-8 bg-primary-950 text-white hover:-translate-y-0.5 hover:bg-primary-800">
          M'écrire un email
          <fa icon="arrow-right" class="text-secondary" />
        </a>
      </div>

      <ul class="flex flex-col gap-4">
        <li v-for="channel in channels" :key="channel.label">
          <a
            :href="channel.href"
            target="_blank"
            rel="noopener"
            class="group flex items-center gap-5 rounded-2xl bg-white p-5 shadow-sm ring-1 ring-primary-100 transition duration-300 hover:-translate-y-0.5 hover:shadow-lg hover:ring-secondary/60"
          >
            <span class="flex h-12 w-12 shrink-0 items-center justify-center rounded-xl bg-primary-950 text-secondary">
              <fa :icon="channel.icon" />
            </span>
            <span class="min-w-0 flex-1">
              <span class="block text-xs font-semibold uppercase tracking-[0.15em] text-primary-400">{{ channel.label }}</span>
              <span class="mt-1 block truncate font-medium text-primary-950">{{ channel.value }}</span>
            </span>
            <fa icon="arrow-right" class="text-primary-300 transition group-hover:translate-x-1 group-hover:text-secondary" />
          </a>
        </li>
      </ul>
    </div>
  </section>
</template>
