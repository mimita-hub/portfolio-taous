<template>
  <div class="min-h-screen bg-linear-to-br from-gray-900 via-blue-900 to-gray-900">
    <NavBar />
    <Hero />
    <Services />
    <Skills />
    <Experience />
    <Projects />
    <Contact />
    <Footer />
  </div>
</template>

<script>
import AOS from 'aos';
import 'aos/dist/aos.css';
import NavBar from './components/NavBar.vue';
import Hero from './components/Hero.vue';
import Services from './components/Services.vue';
import Projects from './components/Projects.vue';
import Footer from './components/Footer.vue';
import Contact from './components/Contact.vue';
import Skills from './components/Skills.vue';
import Experience from './components/Experience.vue';
import { nextTick, onMounted, ref } from 'vue';

export default
  {
    components:
    {
      NavBar,
      Hero,
      Skills,
      Experience,
      Services,
      Projects,
      Contact,
      Footer,
    },

    setup() {
      const loading = ref(true);
      onMounted(async () => {
        await nextTick();

        AOS.init(
          {
            duration: 800,
            once: true,
            offset: 100,
            easing: 'ease-in-out',
          });
        setTimeout(() => {
          loading.value = false;
        }, 800);
      });
      return { loading };

    }
  }
</script>

<style></style>