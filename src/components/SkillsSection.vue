<!-- <template>
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
         { name: "JavaScript", icon: "fab fa-js", color: "#ffe699" },      // pale yellow
        { name: "Angular", icon: "fab fa-angular", color: "#e69ba8" },    // soft red
        { name: "Vue.js", icon: "fab fa-vuejs", color: "#a4dbc6" },       // mint
        { name: "Node.js", icon: "fab fa-node-js", color: "#b7e5b4" },    // soft green
        { name: "Express", icon: "fas fa-server", color: "#e0e0e0" },     // light gray
        { name: "NestJS", icon: "fas fa-feather-alt", color: "#f4b5c3" }, // light rose
        { name: "SCSS", icon: "fab fa-sass", color: "#e5b3cf" },          // pastel pink
        { name: "Bootstrap", icon: "fab fa-bootstrap", color: "#b8a9d6" },// light purple
        { name: "Material UI", icon: "fas fa-cube", color: "#89d7e6" },   // muted cyan
        { name: "PrimeNG", icon: "fas fa-leaf", color: "#b1e4d7" },       // light teal
       
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
</style> -->




















<template>
  <section id="skills" class="skills-section">
    <h2 class="section-title">
      <span class="title-gradient">My Skills</span>
      <div class="title-underline"></div>
    </h2>
    
    <!-- Carousel Controls -->
    <div class="carousel-controls">
      <button 
        v-for="(view, index) in carouselViews" 
        :key="view"
        :class="['control-btn', { active: currentView === index }]"
        @click="setView(index)"
      >
        {{ view }}
      </button>
    </div>

    <!-- Main Carousel Container -->
    <div class="carousel-wrapper" ref="carouselWrapper">
      
      <!-- Infinite Scroll View -->
      <div v-if="currentView === 0" class="infinite-scroll-container">
        <div class="infinite-scroll" :style="{ animationDuration: scrollSpeed + 's' }">
          <div v-for="skill in [...skills, ...skills]" :key="skill.name + Math.random()" class="skill-card">
            <div class="card-inner" :style="{ '--card-color': skill.color }">
              <i :class="skill.icon" class="skill-icon"></i>
              <span class="skill-name">{{ skill.name }}</span>
              <div class="skill-glow"></div>
            </div>
          </div>
        </div>
      </div>

      <!-- 3D Rotating Carousel -->
      <!-- <div v-if="currentView === 1" class="rotating-carousel">
        <div class="carousel-3d" :style="{ transform: `rotateY(${rotation}deg)` }">
          <div 
            v-for="(skill, index) in skills" 
            :key="skill.name"
            class="carousel-item"
            :style="{ 
              transform: `rotateY(${index * (360/skills.length)}deg) translateZ(280px)`,
              '--item-color': skill.color 
            }"
            @click="onSkillClick(skill.name)"
          >
            <div class="item-content">
              <i :class="skill.icon" class="skill-icon-3d"></i>
              <span class="skill-name-3d">{{ skill.name }}</span>
            </div>
          </div>
        </div>
        <div class="carousel-3d-controls">
          <button @click="rotate3D(-1)" class="rotate-btn prev">‹</button>
          <button @click="rotate3D(1)" class="rotate-btn next">›</button>
        </div>
      </div> -->

      <!-- Hexagon Grid -->
      <div v-if="currentView === 1" class="hexagon-grid">
        <div 
          v-for="(skill, index) in skills" 
          :key="skill.name"
          class="hexagon-item"
          :style="{ 
            '--hex-color': skill.color,
            '--delay': index * 0.1 + 's'
          }"
          @click="onSkillClick(skill.name)"
        >
          <div class="hexagon">
            <div class="hexagon-inner">
              <i :class="skill.icon" class="hex-icon"></i>
              <span class="hex-name">{{ skill.name }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Floating Particles -->
      <div v-if="currentView === 2" class="particles-container">
        <div 
          v-for="(skill, index) in skills" 
          :key="skill.name"
          class="particle-skill"
          :style="{ 
            '--particle-color': skill.color,
            '--float-delay': index * 0.3 + 's',
            '--float-duration': (3 + Math.random() * 2) + 's'
          }"
          @click="onSkillClick(skill.name)"
        >
          <div class="particle-orb">
            <i :class="skill.icon" class="particle-icon"></i>
            <span class="particle-name">{{ skill.name }}</span>
            <div class="particle-ring"></div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "SkillsCarousel",
  data() {
    return {
      currentView: 0,
      carouselViews: ['Infinite Scroll', 'Hexagon Grid', 'Floating Orbs'],
      // carouselViews: ['Infinite Scroll', '3D Carousel', 'Hexagon Grid', 'Floating Orbs'],
      scrollSpeed: 20,
      rotation: 0,
      autoRotate: null,
      skills: [
        { name: "HTML", icon: "fab fa-html5", color: "#f6b08a" },
        { name: "CSS", icon: "fab fa-css3-alt", color: "#90b4f6" },
        { name: "JavaScript", icon: "fab fa-js", color: "#ffe699" },
        { name: "Angular", icon: "fab fa-angular", color: "#e69ba8" },
        { name: "Vue.js", icon: "fab fa-vuejs", color: "#a4dbc6" },
        { name: "Node.js", icon: "fab fa-node-js", color: "#b7e5b4" },
        { name: "Express", icon: "fas fa-server", color: "#e0e0e0" },
        { name: "NestJS", icon: "fas fa-feather-alt", color: "#f4b5c3" },
        { name: "SCSS", icon: "fab fa-sass", color: "#e5b3cf" },
        { name: "Bootstrap", icon: "fab fa-bootstrap", color: "#b8a9d6" },
        { name: "Material UI", icon: "fas fa-cube", color: "#89d7e6" },
        { name: "PrimeNG", icon: "fas fa-leaf", color: "#b1e4d7" },
        { name: "Git", icon: "fab fa-git-alt", color: "#f6b4a4" },
        { name: "GitHub", icon: "fab fa-github", color: "#e0e0e0" },
      ],
    };
  },
  mounted() {
    this.startAutoRotation();
  },
  beforeDestroy() {
    if (this.autoRotate) {
      clearInterval(this.autoRotate);
    }
  },
  methods: {
    setView(index) {
      this.currentView = index;
      if (index === 1) {
        this.startAutoRotation();
      } else {
        this.stopAutoRotation();
      }
    },
    onSkillClick(skillName) {
      // Emit skill selection event
      this.$emit('skill-selected', skillName);
      console.log(`Selected skill: ${skillName}`);
    },
    rotate3D(direction) {
      this.rotation += direction * (360 / this.skills.length);
    },
    startAutoRotation() {
      this.stopAutoRotation();
      this.autoRotate = setInterval(() => {
        this.rotation += 360 / this.skills.length;
      }, 3000);
    },
    stopAutoRotation() {
      if (this.autoRotate) {
        clearInterval(this.autoRotate);
        this.autoRotate = null;
      }
    }
  },
};
</script>

<style scoped>
.skills-section {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f0f23 100%);
  padding: 5rem 0;
  min-height: 60vh;
  position: relative;
  overflow: hidden;
}

.skills-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  /* background: radial-gradient(circle at 30% 70%, rgba(125, 211, 252, 0.1) 0%, transparent 50%),
              radial-gradient(circle at 70% 30%, rgba(168, 85, 247, 0.1) 0%, transparent 50%); */
              background:black;
  pointer-events: none;
}

.section-title {
  text-align: center;
  margin-bottom: 3rem;
  position: relative;
}

.title-gradient {
  background: linear-gradient(45deg, #7dd3fc, #a855f7, #ec4899);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-size: 3rem;
  font-weight: 700;
  letter-spacing: 2px;
}

.title-underline {
  width: 100px;
  height: 4px;
  background: linear-gradient(90deg, #7dd3fc, #a855f7);
  margin: 1rem auto;
  border-radius: 2px;
}

/* Carousel Controls */
.carousel-controls {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
}

.control-btn {
  padding: 0.75rem 1.5rem;
  background: rgba(255, 255, 255, 0.1);
  border: 2px solid transparent;
  color: #7dd3fc;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.control-btn:hover, .control-btn.active {
  background: rgba(125, 211, 252, 0.2);
  border-color: #7dd3fc;
  transform: translateY(-2px);
}

.carousel-wrapper {
  position: relative;
  height: 400px;
  max-width: 1200px;
  margin: 0 auto;
}

/* Infinite Scroll Carousel */
.infinite-scroll-container {
  width: 100%;
  overflow: hidden;
  height: 100%;
  display: flex;
  align-items: center;
}

.infinite-scroll {
  display: flex;
  animation: scroll linear infinite;
  gap: 2rem;
}

@keyframes scroll {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

.skill-card {
  flex-shrink: 0;
  min-width: 200px;
}

.card-inner {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(15px);
  border: 2px solid var(--card-color);
  border-radius: 20px;
  padding: 2rem;
  text-align: center;
  position: relative;
  transition: all 0.4s ease;
}

.card-inner:hover {
  transform: translateY(-10px) scale(1.05);
  background: var(--card-color);
  color: #1a1a2e;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
}

.skill-icon {
  font-size: 3rem;
  display: block;
  margin-bottom: 1rem;
  color: var(--card-color);
}

.card-inner:hover .skill-icon {
  color: #1a1a2e;
}

.skill-name {
  font-size: 1.2rem;
  font-weight: 600;
  color: #fff;
}

.card-inner:hover .skill-name {
  color: #1a1a2e;
}

/* 3D Rotating Carousel */
.rotating-carousel {
  width: 100%;
  height: 100%;
  perspective: 1000px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.carousel-3d {
  position: relative;
  width: 200px;
  height: 200px;
  transform-style: preserve-3d;
  transition: transform 0.6s ease;
}

.carousel-item {
  position: absolute;
  width: 150px;
  height: 150px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(15px);
  border: 2px solid var(--item-color);
  border-radius: 15px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.carousel-item:hover {
  background: var(--item-color);
  transform: rotateY(var(--rotation)) translateZ(300px) scale(1.1) !important;
}

.item-content {
  text-align: center;
  color: #fff;
}

.skill-icon-3d {
  font-size: 2.5rem;
  display: block;
  margin-bottom: 0.5rem;
  color: var(--item-color);
}

.carousel-item:hover .skill-icon-3d {
  color: #1a1a2e;
}

.skill-name-3d {
  font-size: 1rem;
  font-weight: 600;
}

.carousel-item:hover .skill-name-3d {
  color: #1a1a2e;
}

.carousel-3d-controls {
  position: absolute;
  bottom: -50px;
  display: flex;
  gap: 1rem;
}

.rotate-btn {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: rgba(125, 211, 252, 0.2);
  border: 2px solid #7dd3fc;
  color: #7dd3fc;
  font-size: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.rotate-btn:hover {
  background: #7dd3fc;
  color: #1a1a2e;
  transform: scale(1.1);
}

/* Hexagon Grid */
.hexagon-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  height: 100%;
  align-content: center;
}

.hexagon-item {
  animation: hexFloat 2s ease-in-out infinite var(--delay);
}

@keyframes hexFloat {
  0%, 100% { transform: translateY(0) rotate(0deg); }
  50% { transform: translateY(-20px) rotate(5deg); }
}

.hexagon {
  width: 120px;
  height: 104px;
  background: var(--hex-color);
  position: relative;
  cursor: pointer;
  transition: all 0.3s ease;
}

.hexagon:before,
.hexagon:after {
  content: "";
  position: absolute;
  width: 0;
  border-left: 60px solid transparent;
  border-right: 60px solid transparent;
}

.hexagon:before {
  bottom: 100%;
  border-bottom: 30px solid var(--hex-color);
}

.hexagon:after {
  top: 100%;
  border-top: 30px solid var(--hex-color);
}

.hexagon-inner {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  color: #1a1a2e;
  text-align: center;
}

.hex-icon {
  font-size: 2rem;
  margin-bottom: 0.5rem;
}

.hex-name {
  font-size: 0.9rem;
  font-weight: 600;
}

.hexagon-item:hover .hexagon {
  transform: scale(1.1) rotate(180deg);
}

/* Floating Particles */
.particles-container {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  gap: 2rem;
}

.particle-skill {
  animation: float var(--float-duration) ease-in-out infinite var(--float-delay);
}

@keyframes float {
  0%, 100% { 
    transform: translateY(0) translateX(0) rotate(0deg); 
  }
  25% { 
    transform: translateY(-30px) translateX(20px) rotate(90deg); 
  }
  50% { 
    transform: translateY(-10px) translateX(-15px) rotate(180deg); 
  }
  75% { 
    transform: translateY(-40px) translateX(10px) rotate(270deg); 
  }
}

.particle-orb {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, var(--particle-color), rgba(0,0,0,0.8));
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  position: relative;
  transition: all 0.3s ease;
  box-shadow: 0 0 30px var(--particle-color);
}

.particle-orb:hover {
  transform: scale(1.2);
  box-shadow: 0 0 50px var(--particle-color);
}

.particle-icon {
  font-size: 1.8rem;
  color: #fff;
  margin-bottom: 0.3rem;
}

.particle-name {
  font-size: 0.8rem;
  color: #fff;
  font-weight: 600;
}

.particle-ring {
  position: absolute;
  width: 120px;
  height: 120px;
  border: 2px solid var(--particle-color);
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
  opacity: 0.6;
}

@keyframes pulse {
  0% { transform: scale(1); opacity: 0.6; }
  50% { transform: scale(1.2); opacity: 0.3; }
  100% { transform: scale(1); opacity: 0.6; }
}

/* Responsive Design */
@media (max-width: 768px) {
  .title-gradient {
    font-size: 2rem;
  }
  
  .carousel-controls {
    flex-wrap: wrap;
    gap: 0.5rem;
  }
  
  .control-btn {
    font-size: 0.9rem;
    padding: 0.5rem 1rem;
  }
  
  .carousel-wrapper {
    height: 300px;
  }
  
  .skill-card {
    min-width: 150px;
  }
  
  .card-inner {
    padding: 1.5rem;
  }
  
  .carousel-item {
    width: 120px;
    height: 120px;
  }
  
  .hexagon {
    width: 80px;
    height: 69px;
  }
  
  .hexagon:before,
  .hexagon:after {
    border-left: 40px solid transparent;
    border-right: 40px solid transparent;
  }
  
  .particle-orb {
    width: 80px;
    height: 80px;
  }
}
</style>