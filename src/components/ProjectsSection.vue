<template>
  <section id="projects" class="projects-section">
    <h2 class="section-title">Projects</h2>
    <div class="projects-grid">
      <transition-group name="fade" tag="div" class="projects-list">
        <div v-for="(project, idx) in projects"
             :key="project.title"
             class="project-card"
             v-observe-visibility="{
                callback: (isVisible) => onVisibilityChange(isVisible, idx),
                once: true
             }"
             :class="{ appear: project.visible }"
             @mousemove="onMouseMove($event, idx)"
             @mouseleave="onMouseLeave(idx)"
             :style="project.cardStyle"
        >
          <img :src="project.image" :alt="project.title" class="project-img" />
          <div class="project-info">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
          </div>
          <transition name="fade">
            <div class="project-overlay" v-if="hoverIdx === idx"
                @mouseleave="hoverIdx = -1">
              <div class="tech-stack">
                <span v-for="tech in project.tech" :key="tech">{{ tech }}</span>
              </div>
              <div class="project-links">
                <a :href="project.github" target="_blank" class="btn small">GitHub</a>
                <a v-if="project.demo" :href="project.demo" target="_blank" class="btn small secondary">Demo</a>
              </div>
            </div>
          </transition>
          <div class="project-hover-catcher" @mouseenter="hoverIdx = idx"></div>
        </div>
      </transition-group>
    </div>
  </section>
</template>

<script>
import { ObserveVisibility } from 'vue-observe-visibility'
export default {
  name: "ProjectsSection",
  directives: { ObserveVisibility },
  data() {
    return {
      hoverIdx: -1,
      projects: [
        {
          title: "Portfolio Website",
          image: "https://dummyimage.com/360x210/18181b/7dd3fc&text=Portfolio",
          description: "A modern, animated, dark-themed Vue.js portfolio.",
          tech: ["Vue", "CSS3", "GSAP"],
          github: "https://github.com/yourusername/portfolio",
          demo: "#",
          visible: false,
          cardStyle: {},
        },
        {
          title: "Task Manager App",
          image: "https://dummyimage.com/360x210/23232a/0ea5e9&text=Tasks+App",
          description: "A productive, mobile-friendly task organizer.",
          tech: ["Vue", "Node.js", "MongoDB"],
          github: "https://github.com/yourusername/taskmanager",
          demo: "#",
          visible: false,
          cardStyle: {},
        },
        // Add more projects as needed!
      ],
    };
  },
  methods: {
    onVisibilityChange(isVisible, idx) {
      if (isVisible) this.$set(this.projects[idx], 'visible', true);
    },
    onMouseMove(e, idx) {
      const card = e.currentTarget;
      const rect = card.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      // Calculate rotation
      const rotateY = ((x / rect.width) - 0.5) * 16;
      const rotateX = ((y / rect.height) - 0.5) * -16;
      const shadowX = ((x / rect.width) - 0.5) * 16;
      const shadowY = ((y / rect.height) - 0.5) * 16;
      this.$set(this.projects[idx], 'cardStyle', {
        transform: `perspective(700px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.035)`,
        boxShadow: `${-shadowX}px ${shadowY}px 32px 0 #0ea5e944, 0 1.5px 5px #2563eb55`
      });
    },
    onMouseLeave(idx) {
      this.$set(this.projects[idx], 'cardStyle', {
        transform: 'none',
        boxShadow: '0 4px 24px #0000003a'
      });
    }
  },
};
</script>

<style scoped>
.projects-section {
  background: #18181b;
  padding: 4rem 0 3rem 0;
}
.section-title {
  text-align: center;
  color: #7dd3fc;
  font-size: 2.1rem;
  margin-bottom: 2.4rem;
  letter-spacing: 1px;
}
.projects-grid {
  display: flex;
  justify-content: center;
}
.projects-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1.4rem;
  width: 95vw;
  max-width: 900px;
}
.project-card {
  background: #23232a;
  border-radius: 14px;
  box-shadow: 0 4px 24px #0000003a;
  overflow: hidden;
  position: relative;
  transition: 
    transform 0.18s cubic-bezier(.25,.8,.25,1),
    box-shadow 0.18s cubic-bezier(.25,.8,.25,1);
  cursor: pointer;
  opacity: 0;
  transform: translateY(60px) scale(0.98);
  min-width: 0;
  will-change: transform, box-shadow;
}
.project-card.appear {
  opacity: 1;
  transform: none;
  transition: opacity 0.8s cubic-bezier(0.25,1,0.5,1), transform 0.8s cubic-bezier(0.25,1,0.5,1);
}
.project-img {
  width: 100%;
  height: 145px;
  object-fit: cover;
  background: #23232a;
  transition: filter 0.27s cubic-bezier(.25,.8,.25,1);
}
.project-card:hover .project-img {
  filter: brightness(1.12) saturate(1.15) blur(1.5px);
}
.project-info {
  padding: 1.1rem 0.8rem 0.8rem 0.8rem;
}
.project-info h3 {
  color: #7dd3fc;
  margin-bottom: 0.4rem;
  font-size: 1.09rem;
}
.project-info p {
  color: #d1d5db;
  font-size: 0.91rem;
  margin-bottom: 0.5rem;
}
.project-hover-catcher {
  position: absolute;
  inset: 0;
  z-index: 3;
}
.project-overlay {
  position: absolute;
  inset: 0;
  background: rgba(24, 24, 32, 0.98);
  color: #fff;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  z-index: 4;
  animation: fadeIn 0.44s;
  padding: 1.2rem;
  gap: 0.8rem;
}
@keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.7rem;
  margin-bottom: 0.6rem;
}
.tech-stack span {
  background: #18181b;
  color: #7dd3fc;
  padding: 0.27rem 0.61rem;
  border-radius: 8px;
  font-size: 0.89rem;
  font-weight: 600;
}
.project-links {
  display: flex;
  gap: 1.1rem;
}
.btn.small {
  padding: 0.37rem 1.15rem;
  font-size: 0.95rem;
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
.fade-enter-active, .fade-leave-active { transition: opacity 0.5s; }
.fade-enter, .fade-leave-to { opacity: 0; }
@media (max-width: 700px) {
  .projects-list { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 500px) {
  .projects-list { grid-template-columns: 1fr; }
}
</style>