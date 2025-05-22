<template>
  <section id="skills" class="skills-section">
    <h2 class="section-title">My Skills</h2>
    <div class="skills-buttons">
      <button
        v-for="skill in skills"
        :key="skill.name"
        class="skill-btn"
        :style="{ '--btn-color': skill.color }"
        @click="onSkillClick(skill.name)"
      >
        <i :class="skill.icon"></i>
        <span>{{ skill.name }}</span>
      </button>
    </div>
  </section>
</template>

<script>
export default {
  name: "SkillsSection",
  data() {
    return {
      skills: [
        { name: "HTML", icon: "fab fa-html5", color: "#f6b08a" },         // softer orange
        { name: "CSS", icon: "fab fa-css3-alt", color: "#90b4f6" },       // soft blue
        { name: "SCSS", icon: "fab fa-sass", color: "#e5b3cf" },          // pastel pink
        { name: "Bootstrap", icon: "fab fa-bootstrap", color: "#b8a9d6" },// light purple
        { name: "Material UI", icon: "fas fa-cube", color: "#89d7e6" },   // muted cyan
        { name: "PrimeNG", icon: "fas fa-leaf", color: "#b1e4d7" },       // light teal
        { name: "JavaScript", icon: "fab fa-js", color: "#ffe699" },      // pale yellow
        { name: "Angular", icon: "fab fa-angular", color: "#e69ba8" },    // soft red
        { name: "Vue.js", icon: "fab fa-vuejs", color: "#a4dbc6" },       // mint
        { name: "Node.js", icon: "fab fa-node-js", color: "#b7e5b4" },    // soft green
        { name: "Express", icon: "fas fa-server", color: "#e0e0e0" },     // light gray
        { name: "NestJS", icon: "fas fa-feather-alt", color: "#f4b5c3" }, // light rose
        { name: "Git", icon: "fab fa-git-alt", color: "#f6b4a4" },        // coral
        { name: "GitHub", icon: "fab fa-github", color: "#e0e0e0" },      // light gray
      ],
    };
  },
  methods: {
    onSkillClick(skillName) {
      alert(`You clicked: ${skillName}`);
    },
  },
};
</script>

<style scoped>
.skills-section {
  background: #23232a;
  padding: 4.5rem 0 3.5rem 0;
}
.section-title {
  text-align: center;
  color: #7dd3fc;
  font-size: 2.1rem;
  margin-bottom: 2.4rem;
  letter-spacing: 1px;
}
.skills-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 1.3rem;
  justify-content: center;
  align-items: center;
  max-width: 900px;
  margin: 0 auto;
}
.skill-btn {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  background: rgba(35,35,42, 0.95);
  border: 2px solid var(--btn-color, #7dd3fc);
  color: var(--btn-color, #7dd3fc);
  border-radius: 12px;
  font-size: 1.08rem;
  font-weight: 600;
  padding: 0.65rem 1.3rem;
  cursor: pointer;
  box-shadow: 0 4px 16px #0001;
  transition: 
    background 0.13s,
    color 0.13s,
    border-color 0.13s,
    transform 0.15s;
}
.skill-btn i {
  font-size: 1.44rem;
  vertical-align: middle;
  filter: brightness(0.96) contrast(0.95);
}
.skill-btn:hover, .skill-btn:focus {
  background: var(--btn-color, #7dd3fc);
  color: #23232a !important;
  border-color: #fff;
  transform: translateY(-4px) scale(1.07);
  outline: none;
}
.skill-btn:hover i {
  filter: brightness(0.8) contrast(1.15);
}
@media (max-width: 700px) {
  .skills-buttons {
    gap: 0.8rem;
  }
  .skill-btn {
    font-size: 0.98rem;
    padding: 0.5rem 1rem;
  }
  .skill-btn i {
    font-size: 1.15rem;
  }
}
@media (max-width: 450px) {
  .skills-buttons {
    gap: 0.5rem;
  }
  .skill-btn {
    font-size: 0.9rem;
    padding: 0.45rem 0.82rem;
  }
}
</style>