<script setup>
const base = `${import.meta.env.BASE_URL}images/skills/`;

const skills = [
  { src: `${base}html.svg`, name: "HTML" },
  { src: `${base}css.svg`, name: "CSS" },
  { src: `${base}php.svg`, name: "PHP" },
  { src: `${base}laravel.svg`, name: "Laravel" },
  { src: `${base}vue.svg`, name: "Vue.js" },
  { src: `${base}react.svg`, name: "React" },
  { src: `${base}nodejs.svg`, name: "Node.js" },
  { src: `${base}java.svg`, name: "Java" },
  { src: `${base}flutter-svgrepo-com.svg`, name: "Flutter" },
];
</script>

<template>
  <section class="w-full border-y border-primary-100 bg-white py-12" aria-labelledby="skills-title">
    <p id="skills-title" class="text-center text-xs font-semibold uppercase tracking-[0.25em] text-primary-400">
      Technologies que j'utilise
    </p>

    <div
      class="group relative mt-8 flex overflow-hidden [mask-image:linear-gradient(to_right,transparent,black_12%,black_88%,transparent)]"
    >
      <ul
        v-for="copy in 2"
        :key="copy"
        class="flex shrink-0 animate-infinite-scroll items-center group-hover:[animation-play-state:paused]"
        :aria-hidden="copy === 2 ? 'true' : undefined"
      >
        <li
          v-for="skill in skills"
          :key="skill.name"
          class="mx-8 flex flex-col items-center gap-2 sm:mx-12"
        >
          <img
            :src="skill.src"
            :alt="copy === 1 ? skill.name : ''"
            class="h-12 w-auto max-w-none opacity-60 grayscale transition duration-300 hover:opacity-100 hover:grayscale-0"
            loading="lazy"
          />
        </li>
      </ul>
    </div>
  </section>
</template>
