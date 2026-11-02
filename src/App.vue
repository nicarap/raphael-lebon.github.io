<script setup>
import Skills from './components/Skills.vue';
import Footer from './components/Footer.vue';
import Profil from './components/Profil.vue';
import Navigation from "./components/Navigation.vue";
import Contact from "./components/Contact.vue";
import Home from "./components/Home.vue";
import Projects from "./components/Projects.vue";
</script>

<template>
  <Navigation />
  <main class="w-full overflow-x-clip">
    <Home />
    <Profil />
    <Skills />
    <Projects />
    <Contact />
  </main>
  <Footer />
</template>
