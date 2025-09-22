
<template>
  <div id="app" class="dark-theme">
    <HeaderBar />
    <HeroSection id="hero" />
    <SkillsSection id="skills" />
    <ProjectsSection id="projects" />
    <ContactSection id="contact" />
    <FooterBar />
  </div>
</template>

<script>
import HeaderBar from './components/HeaderBar.vue'
import HeroSection from './components/HeroSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterBar from './components/FooterBar.vue'

export default {
  name: 'App',
  components: {
    HeaderBar,
    HeroSection,
    SkillsSection,
    ProjectsSection,
    ContactSection,
    FooterBar
  },
  mounted() {
    // Load particles.js if needed
    if (!window.particlesJS && typeof window !== "undefined") {
      const script = document.createElement("script");
      script.src = "https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js";
      document.body.appendChild(script);
    }
  }
}
</script>

<style>
.dark-theme {
  /* background: #18181b; */
  background: black;
  color: #f3f3f3;
  min-height: 100vh;
  /* font-family: 'Segoe UI', Arial, sans-serif; */
  font-family: 'Roboto', Arial, sans-serif;
  overflow-x: hidden;
}
html {
  scroll-behavior: smooth;
}
body {
  margin: 0;
  padding: 0;
  /* background: #18181b; */
  background: black;
}
</style>
