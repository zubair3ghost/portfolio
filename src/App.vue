
<template>
  <div id="app" class="dark-theme">
    <HeaderBar />
    <HeroSection />
    <SkillsSection />
    <ProjectsSection />
    <ContactSection />
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
  background: #18181b;
  color: #f3f3f3;
  min-height: 100vh;
  font-family: 'Segoe UI', Arial, sans-serif;
  overflow-x: hidden;
}
html {
  scroll-behavior: smooth;
}
body {
  margin: 0;
  padding: 0;
  background: #18181b;
}
</style>



<!-- <template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->
