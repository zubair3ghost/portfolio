<template>
  <section id="hero" class="hero-section">
    <div id="particles-js" class="hero-bg"></div>
    <div class="hero-content">
      <transition name="fade-slide-down" appear>
        <div class="hero-text">
          <h1>Hi, I'm <span class="accent">M. Developer</span></h1>
          <h2>Frontend Developer</h2>
          <p>Building beautiful, performant web apps & digital experiences.</p>
          <div class="hero-actions">
            <a :href="resumeUrl" class="btn" download>Download Resume</a>
            <a href="#contact" class="btn secondary">Contact Me</a>
          </div>
        </div>
      </transition>
      <transition name="fade-slide-up" appear>
        <div class="hero-img">
          <img src="https://dummyimage.com/350x350/23232a/7dd3fc&text=Your+Photo" alt="Avatar">
        </div>
      </transition>
    </div>
  </section>
</template>

<script>
export default {
  name: "HeroSection",
  data() {
    return {
      resumeUrl: "#", // Replace with your resume link
    };
  },
  mounted() {
    if (window.particlesJS) {
      window.particlesJS.load('particles-js', 'particles.json', function() {});
    }
  },
};
</script>

<style scoped>
.hero-section {
  position: relative;
  min-height: 70vh;
  background: #18181b;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}
.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 1;
  background: #18181b;
}
.hero-content {
  position: relative;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2.5rem;
  width: 95vw;
  max-width: 1100px;
  margin: 0 auto;
  flex-wrap: wrap;
}
.hero-text {
  flex: 1 1 340px;
  color: #f3f3f3;
  animation: floatInDown 1s;
}
.hero-text h1 {
  font-size: 2.7rem;
  margin-bottom: 0.2rem;
  font-weight: bold;
  color: #fff;
}
.hero-text .accent {
  color: #7dd3fc;
}
.hero-text h2 {
  font-size: 1.6rem;
  color: #7dd3fc;
  margin-bottom: 1rem;
}
.hero-text p {
  color: #d1d5db;
  font-size: 1.1rem;
  margin-bottom: 1.5rem;
}
.hero-actions {
  display: flex;
  gap: 1.5rem;
}
.btn {
  background: linear-gradient(90deg,#0ea5e9 0%,#7dd3fc 100%);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  padding: 0.7rem 1.7rem;
  font-size: 1rem;
  text-decoration: none;
  box-shadow: 0 4px 16px 0 #2563eb33;
  transition: background 0.2s, transform 0.15s;
}
.btn:hover {
  background: linear-gradient(90deg,#7dd3fc 0%,#0ea5e9 100%);
  transform: translateY(-2px) scale(1.04);
}
.btn.secondary {
  background: transparent;
  border: 2px solid #7dd3fc;
  color: #7dd3fc;
}
.btn.secondary:hover {
  background: #23232a;
  color: #fff;
}
.hero-img {
  flex: 1 1 300px;
  display: flex;
  align-items: center;
  justify-content: center;
  animation: floatInUp 1.2s;
}
.hero-img img {
  width: 320px;
  max-width: 90vw;
  border-radius: 20px;
  box-shadow: 0 8px 32px 0 #0ea5e977;
  transition: transform 0.25s;
}
.hero-img img:hover {
  transform: scale(1.04) rotate(-1deg);
}

@media (max-width: 900px) {
  .hero-content {
    flex-direction: column-reverse;
    gap: 2.5rem;
    align-items: center;
  }
  .hero-text, .hero-img {
    flex: 1 1 100%;
    text-align: center;
    justify-content: center;
  }
  .hero-img img {
    margin: 0 auto;
  }
}
@media (max-width: 500px) {
  .hero-text h1 { font-size: 1.4rem; }
  .hero-text h2 { font-size: 1rem; }
  .hero-img img { width: 160px; }
}

/* Animations */
@keyframes floatInDown { from { opacity:0; transform:translateY(-60px);} to { opacity:1; transform:none;} }
@keyframes floatInUp { from { opacity:0; transform:translateY(60px);} to { opacity:1; transform:none;} }
.fade-slide-down-enter-active, .fade-slide-down-appear-active { animation: floatInDown 1.1s; }
.fade-slide-up-enter-active, .fade-slide-up-appear-active { animation: floatInUp 1.1s; }
</style>
