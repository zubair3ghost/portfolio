
<template>
  <section id="hero" class="hero-section">
    <div id="particles-js" class="hero-bg"></div>
    <div class="hero-overlay"></div>
    
    <div class="hero-content">
      <div class="container">
        <div class="hero-layout">
          <transition name="fade-slide-down" appear>
            <div class="hero-text">
              <div class="greeting">
                <span class="wave">👋</span>
                <span class="greeting-text">Hello, I'm</span>
              </div>
              
              <h1 class="hero-title">
              
                <span class="title-highlight">Website Developer</span>
              </h1>
              
              <div class="hero-subtitle">
                <span class="typing-text">{{ currentText }}</span>
                <span class="cursor">|</span>
              </div>
              
              <p class="hero-description">
                Passionate about crafting exceptional digital experiences through clean, 
                efficient code and innovative design. I specialize in modern web technologies 
                and love turning complex problems into simple, beautiful solutions.
              </p>
          
              
              <div class="hero-actions">
                <a :href="resumeUrl" class="btn primary" download>
                  <i class="icon-download"></i>
                  Download Resume
                </a>
                <a href="#projects" class="btn ghost">
                  <i class="icon-eye"></i>
                  View Work
                </a>
              </div>
            </div>
          </transition>
          
          <transition name="fade-slide-up" appear>
            <div class="hero-visual">
              <div class="hero-img-container">
                <div class="img-frame">
                  <div class="img-bg-effect"></div>
                  <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=400&h=400&fit=crop&crop=face" alt="M. Developer" class="hero-img">
                  <div class="img-overlay"></div>
                </div>
                
              </div>
            </div>
          </transition>
        </div>
        
        <transition name="fade-up" appear>
          <div class="scroll-indicator">
            <div class="scroll-arrow">
              <div class="arrow-line"></div>
              <div class="arrow-head"></div>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'HeroSection',
  data() {
    return {
      resumeUrl: '/path/to/your/resume.pdf',
      typingTexts: [
        'Building Amazing Web Experiences',
        'Creating Responsive Designs',
        'Developing Modern Applications',
        'Solving Complex Problems'
      ],
      currentTextIndex: 0,
      currentText: '',
      isDeleting: false,
      typeSpeed: 100,
      deleteSpeed: 50,
      pauseTime: 2000
    }
  },
  mounted() {
    this.typeText();
  },
  methods: {
    typeText() {
      const fullText = this.typingTexts[this.currentTextIndex];
      
      if (this.isDeleting) {
        this.currentText = fullText.substring(0, this.currentText.length - 1);
      } else {
        this.currentText = fullText.substring(0, this.currentText.length + 1);
      }
      
      let speed = this.isDeleting ? this.deleteSpeed : this.typeSpeed;
      
      if (!this.isDeleting && this.currentText === fullText) {
        speed = this.pauseTime;
        this.isDeleting = true;
      } else if (this.isDeleting && this.currentText === '') {
        this.isDeleting = false;
        this.currentTextIndex = (this.currentTextIndex + 1) % this.typingTexts.length;
      }
      
      setTimeout(() => this.typeText(), speed);
    }
  }
}
</script>

<!-- <style scoped>
/* CSS Variables */
:root {
  --primary-bg: #0a0a0f;
  --secondary-bg: #1a1a2e;
  --accent-color: #7dd3fc;
  --accent-hover: #0ea5e9;
  --text-primary: #ffffff;
  --text-secondary: #a1a1aa;
  --text-muted: #71717a;
  --border-color: rgba(255, 255, 255, 0.1);
  --glass-bg: rgba(255, 255, 255, 0.05);
  --shadow-glow: rgba(125, 211, 252, 0.3);
}

/* Hero Section */
.hero-section {
  position: relative;
  min-height: 100vh;
  background: linear-gradient(135deg, var(--primary-bg) 0%, var(--secondary-bg) 100%);
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle at 30% 40%, rgba(125, 211, 252, 0.1) 0%, transparent 50%);
  z-index: 2;
}

.hero-content {
  position: relative;
  z-index: 3;
  width: 100%;
  padding: 2rem 0;
}
  
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.9rem;
}

.hero-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  min-height: 80vh;
}

/* Hero Text */
.hero-text {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.greeting {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  /* margin-bottom: 1rem; */
}

.wave {
  font-size: 1.5rem;
  animation: wave 2s ease-in-out infinite;
}

.greeting-text {
  color: var(--text-secondary);
  font-size: 1.1rem;
  font-weight: 500;
}

.hero-title {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  line-height: 1.1;
  margin: 0;
}

.name {
  display: block;
  background: linear-gradient(135deg, var(--text-primary), var(--accent-color));
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.title-highlight {
  display: block;
  color: var(--accent-color);
  font-size: 0.7em;
  font-weight: 600;
  margin-top: 0.5rem;
  opacity: 0.9;
}

.hero-subtitle {
  height: 2rem;
  display: flex;
  align-items: center;
  font-size: 1.2rem;
  color: var(--text-secondary);
  font-weight: 500;
  @media (max-width: 768px) {
    justify-content: center;
  }
}

.typing-text {
  min-height: 1.5rem;
  color: orange;
}

.cursor {
  animation: blink 1s infinite;
  color: var(--accent-color);
  font-weight: 300;
}

.hero-description {
  font-size: 1.1rem;
  line-height: 1.7;
  color: var(--text-secondary);
  /* max-width: 500px; */
}

/* Hero Stats */
.hero-stats {
  display: flex;
  gap: 2rem;
  margin: 1.5rem 0;
}

.stat-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.stat-number {
  font-size: 1.8rem;
  font-weight: 700;
  color: var(--accent-color);
  line-height: 1;
}

.stat-label {
  font-size: 0.9rem;
  color: var(--text-muted);
  margin-top: 0.25rem;
}

/* Hero Actions */
.hero-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin: 2rem 0;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.875rem 1.75rem;
  border-radius: 50px;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  border: 2px solid white;
;
}

.btn.primary {
  background: linear-gradient(135deg, var(--accent-color), var(--accent-hover));
  color: white;
  box-shadow: 0 4px 15px var(--shadow-glow);
}

.btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px var(--shadow-glow);
}

.btn.secondary {
  background: var(--glass-bg);
  color: var(--text-primary);
  border-color: var(--border-color);
  backdrop-filter: blur(10px);
}

.btn.secondary:hover {
  background: rgba(255, 255, 255, 0.1);
  border-color: var(--accent-color);
  transform: translateY(-2px);
}

.btn.ghost {
  background: transparent;
  color: var(--text-secondary);
  border-color: var(--border-color);
}

.btn.ghost:hover {
  color: var(--accent-color);
  border-color: var(--accent-color);
  background: rgba(125, 211, 252, 0.1);
}

/* Social Links */
.social-links {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
}

.social-link {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 2.5rem;
  height: 2.5rem;
  border-radius: 50%;
  background: var(--glass-bg);
  border: 1px solid var(--border-color);
  color: var(--text-secondary);
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  color: var(--accent-color);
  border-color: var(--accent-color);
  background: rgba(125, 211, 252, 0.1);
  transform: translateY(-2px);
}

/* Hero Visual */
.hero-visual {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.hero-img-container {
  position: relative;
  width: 350px;
  height: 350px;
}

.img-frame {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
  border: 3px solid var(--accent-color);
  box-shadow: 0 0 30px var(--shadow-glow);
}

.img-bg-effect {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: conic-gradient(from 0deg, var(--accent-color), transparent, var(--accent-color));
  animation: rotate 8s linear infinite;
  z-index: -1;
}

.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  position: relative;
  z-index: 2;
}

.img-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, transparent 0%, rgba(125, 211, 252, 0.1) 100%);
  z-index: 3;
}

/* Floating Tech Icons */
.floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}

.tech-icon {
  position: absolute;
  width: 60px;
  height: 60px;
  background: var(--glass-bg);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--accent-color);
  backdrop-filter: blur(10px);
  animation: float 3s ease-in-out infinite;
  animation-delay: var(--delay);
}

.tech-icon:nth-child(1) { top: 10%; right: 20%; }
.tech-icon:nth-child(2) { top: 30%; left: -10%; }
.tech-icon:nth-child(3) { bottom: 30%; right: -10%; }
.tech-icon:nth-child(4) { bottom: 10%; left: 20%; }

/* Scroll Indicator */
.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  color: var(--text-muted);
}

.scroll-text {
  font-size: 0.9rem;
  font-weight: 500;
}

.scroll-arrow {
  width: 2px;
  height: 3rem;
  position: relative;
  background: linear-gradient(to bottom, var(--accent-color), transparent);
}

.arrow-head {
  position: absolute;
  bottom: -5px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 8px solid var(--accent-color);
  animation: bounce 2s infinite;
}

/* Animations */
@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(-10deg); }
  20% { transform: rotate(12deg); }
  40% { transform: rotate(-4deg); }
  50% { transform: rotate(10deg); }
  60% { transform: rotate(-6deg); }
  70% { transform: rotate(8deg); }
  80% { transform: rotate(-4deg); }
  90% { transform: rotate(4deg); }
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-15px); }
}

@keyframes bounce {
  0%, 100% { transform: translateX(-50%) translateY(0); }
  50% { transform: translateX(-50%) translateY(10px); }
}

/* Transition Classes */
.fade-slide-down-enter-active { 
  transition: all 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94); 
}
.fade-slide-down-enter-from { 
  opacity: 0; 
  transform: translateY(-50px); 
}

.fade-slide-up-enter-active { 
  transition: all 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94); 
  transition-delay: 0.3s;
}
.fade-slide-up-enter-from { 
  opacity: 0; 
  transform: translateY(50px); 
}

.fade-up-enter-active { 
  transition: all 0.6s ease; 
  transition-delay: 0.6s;
}
.fade-up-enter-from { 
  opacity: 0; 
  transform: translateY(20px); 
}

/* Icon Styles */
.icon-download::before { content: '📥'; margin-right: 0.5rem; }
.icon-message::before { content: '💬'; margin-right: 0.5rem; }
.icon-eye::before { content: '👁️'; margin-right: 0.5rem; }
.icon-linkedin::before { content: '💼'; }
.icon-github::before { content: '⚡'; }
.icon-twitter::before { content: '🐦'; }
.icon-email::before { content: '📧'; }

/* Responsive Design */
@media (max-width: 1024px) {
  .hero-layout {
    gap: 3rem;
  }
  
  .hero-img-container {
    width: 300px;
    height: 300px;
  }
}

@media (max-width: 768px) {
  .hero-layout {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }
  
  .hero-text {
    order: 2;
  }
  
  .hero-visual {
    order: 1;
  }
  
  .hero-img-container {
    width: 250px;
    height: 250px;
  }
  
  .hero-stats {
    justify-content: center;
  }
  
  .hero-actions {
    justify-content: center;
  }
  
  .social-links {
    justify-content: center;
  }
}

@media (max-width: 480px) {
  .container {
   padding: 0 1rem;
  }
  
  .hero-stats {
    gap: 1rem;
  }
  
  .hero-actions {
    flex-direction: column;
    align-items: center;
  }
  
  .btn {
    width: 80%;
    /* max-width: 280px; */
    justify-content: center;
  }
  
  .hero-img-container {
    width: 200px;
    height: 200px;
  }
  
  .tech-icon {
    width: 45px;
    height: 45px;
    font-size: 0.8rem;
  }
}
@media (max-width: 480px) {
  .container {
          margin-top: 2rem;
  }
}
</style> -->


<style scoped >



/* Enhanced CSS with Beautiful Animations */

/* CSS Variables */
:root {
  --primary-bg: #0a0a0f;
  --secondary-bg: #1a1a2e;
  --accent-color: #7dd3fc;
  --accent-hover: #0ea5e9;
  --text-primary: #ffffff;
  --text-secondary: #a1a1aa;
  --text-muted: #71717a;
  --border-color: rgba(255, 255, 255, 0.1);
  --glass-bg: rgba(255, 255, 255, 0.05);
  --shadow-glow: rgba(125, 211, 252, 0.3);
}

/* Enhanced Hero Section with Animations */
.hero-section {
  position: relative;
  min-height: 100vh;
  background: linear-gradient(135deg, var(--primary-bg) 0%, var(--secondary-bg) 100%);
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(
    circle at 20% 80%, 
    rgba(125, 211, 252, 0.15) 0%, 
    transparent 50%
  ),
  radial-gradient(
    circle at 80% 20%, 
    rgba(14, 165, 233, 0.15) 0%, 
    transparent 50%
  );
  animation: backgroundPulse 6s ease-in-out infinite alternate;
  z-index: 1;
}

.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.hero-bg::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    radial-gradient(2px 2px at 20px 30px, rgba(255,255,255,0.3), transparent),
    radial-gradient(2px 2px at 40px 70px, rgba(125, 211, 252, 0.4), transparent),
    radial-gradient(1px 1px at 90px 40px, rgba(255,255,255,0.2), transparent),
    radial-gradient(1px 1px at 130px 80px, rgba(125, 211, 252, 0.3), transparent);
  background-repeat: repeat;
  background-size: 150px 100px;
  animation: sparkle 8s linear infinite;
}

.hero-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(
    circle at 30% 40%, 
    rgba(125, 211, 252, 0.1) 0%, 
    transparent 50%
  );
  z-index: 2;
  animation: overlayShift 10s ease-in-out infinite alternate;
}

.hero-content {
  position: relative;
  z-index: 3;
  width: 100%;
  padding: 2rem 0;
  opacity: 0;
  transform: translateY(30px);
  animation: contentFadeIn 1.2s ease-out 0.3s forwards;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1.9rem;
}

.hero-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  min-height: 80vh;
}

/* Enhanced Hero Text Animations */
.hero-text {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.hero-text > * {
  opacity: 0;
  transform: translateX(-50px);
  animation: slideInLeft 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
}

.hero-text > *:nth-child(1) { animation-delay: 0.5s; }
.hero-text > *:nth-child(2) { animation-delay: 0.7s; }
.hero-text > *:nth-child(3) { animation-delay: 0.9s; }
.hero-text > *:nth-child(4) { animation-delay: 1.1s; }
.hero-text > *:nth-child(5) { animation-delay: 1.3s; }
.hero-text > *:nth-child(6) { animation-delay: 1.5s; }

.greeting {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.wave {
  font-size: 1.5rem;
  animation: wave 2s ease-in-out infinite;
  transform-origin: 70% 70%;
}

.greeting-text {
  color: var(--text-secondary);
  font-size: 1.1rem;
  font-weight: 500;
  position: relative;
}

.greeting-text::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--accent-color), transparent);
  animation: underlineExpand 1s ease-out 1.8s forwards;
}

.hero-title {
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  line-height: 1.1;
  margin: 0;
}

.name {
  display: block;
  background: linear-gradient(135deg, var(--text-primary), var(--accent-color));
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-size: 200% 200%;
  animation: gradientShift 3s ease-in-out infinite alternate;
}

.title-highlight {
  display: block;
  color: var(--accent-color);
  font-size: 0.7em;
  font-weight: 600;
  margin-top: 0.5rem;
  opacity: 0;
  animation: fadeInBounce 0.6s ease-out 1.5s forwards;
}

.title-highlight::before {
  content: '▶ ';
  opacity: 0;
  animation: arrowSlide 0.5s ease-out 2s forwards;
}

.hero-subtitle {
  height: 2rem;
  display: flex;
  align-items: center;
  font-size: 1.2rem;
  color: var(--text-secondary);
  font-weight: 500;
  position: relative;
}

.hero-subtitle::before {
  content: '';
  position: absolute;
  left: -20px;
  top: 50%;
  transform: translateY(-50%);
  width: 15px;
  height: 2px;
  background: var(--accent-color);
  opacity: 0;
  animation: lineSlideIn 0.5s ease-out 1.8s forwards;
}

.typing-text {
  min-height: 1.5rem;
  color: orange;
  position: relative;
}

.typing-text::after {
  content: '';
  position: absolute;
  right: -5px;
  top: 0;
  width: 2px;
  height: 100%;
  background: var(--accent-color);
  animation: typingCursor 1s infinite;
}

.cursor {
  animation: blink 1s infinite;
  color: var(--accent-color);
  font-weight: 300;
  font-size: 1.5em;
}

.hero-description {
  font-size: 1.1rem;
  line-height: 1.7;
  color: var(--text-secondary);
  position: relative;
}

.hero-description::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 0;
  height: 100%;
  background: linear-gradient(90deg, rgba(125, 211, 252, 0.1), transparent);
  animation: textReveal 2s ease-out 2s forwards;
}

/* Enhanced Button Animations */
.hero-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  margin: 2rem 0;
}

.hero-actions .btn {
  opacity: 0;
  transform: translateY(20px) scale(0.9);
  animation: buttonPop 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55) forwards;
}

.hero-actions .btn:nth-child(1) { animation-delay: 2.2s; }
.hero-actions .btn:nth-child(2) { animation-delay: 2.4s; }

.btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.875rem 1.75rem;
  border-radius: 50px;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
  overflow: hidden;
  border: 2px solid white;
}

.btn::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 0;
  height: 0;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  transition: all 0.5s ease;
  z-index: -1;
}

.btn:hover::before {
  width: 300px;
  height: 300px;
}

.btn.primary {
  background: linear-gradient(135deg, var(--accent-color), var(--accent-hover));
  color: white;
  box-shadow: 0 4px 15px var(--shadow-glow);
}

.btn.primary:hover {
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 8px 30px var(--shadow-glow);
}

.btn.primary:active {
  transform: translateY(-1px) scale(1.02);
}

.btn.ghost {
  background: transparent;
  color: var(--text-secondary);
  border-color: var(--border-color);
  position: relative;
}

.btn.ghost::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 2px;
  background: linear-gradient(45deg, var(--accent-color), transparent, var(--accent-color));
  mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask-composite: xor;
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.btn.ghost:hover {
  color: var(--accent-color);
  border-color: var(--accent-color);
  background: rgba(125, 211, 252, 0.1);
  transform: translateY(-2px);
}

.btn.ghost:hover::after {
  opacity: 1;
}

/* Enhanced Hero Visual Animations */
.hero-visual {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  opacity: 0;
  transform: translateX(50px) scale(0.8);
  animation: visualSlideIn 1s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0.8s forwards;
}

.hero-img-container {
  position: relative;
  width: 350px;
  height: 350px;
}

.hero-img-container::before {
  content: '';
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  border-radius: 50%;
  background: conic-gradient(
    from 0deg,
    var(--accent-color) 0deg,
    transparent 90deg,
    var(--accent-color) 180deg,
    transparent 270deg
  );
  animation: rotateGlow 4s linear infinite;
  z-index: -1;
  opacity: 0.7;
}

.hero-img-container::after {
  content: '';
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  border-radius: 50%;
  /* background: linear-gradient(45deg, transparent, rgba(125, 211, 252, 0.2), transparent); */
  background:#7dd3fc;;
  animation: shimmer 2s ease-in-out infinite alternate;
  z-index: -1;
}

.img-frame {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
  border: 3px solid var(--accent-color);
  box-shadow: 
    0 0 30px var(--shadow-glow),
    inset 0 0 20px rgba(125, 211, 252, 0.1);
  animation: imagePulse 3s ease-in-out infinite alternate;
}

.img-bg-effect {
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: conic-gradient(
    from 0deg, 
    var(--accent-color), 
    transparent 120deg, 
    var(--accent-color) 240deg,
    transparent
  );
  animation: rotate 8s linear infinite;
  z-index: 1;
  opacity: 0.3;
}

.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  position: relative;
  z-index: 2;
  transition: transform 0.3s ease;
}

.hero-img:hover {
  transform: scale(1.05);
}

.img-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    135deg, 
    transparent 0%, 
    rgba(125, 211, 252, 0.1) 100%
  );
  z-index: 3;
  transition: opacity 0.3s ease;
}

.img-overlay:hover {
  opacity: 0.7;
}

/* Enhanced Scroll Indicator */
.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  color: var(--text-muted);
  opacity: 0;
  animation: fadeInUp 1s ease-out 3s forwards;
}

.scroll-indicator:hover .scroll-arrow {
  animation-play-state: paused;
  transform: translateY(-5px);
}

.scroll-arrow {
  width: 2px;
  height: 3rem;
  position: relative;
  background: linear-gradient(to bottom, var(--accent-color), transparent);
  transition: transform 0.3s ease;
}

.arrow-line {
  width: 100%;
  height: 100%;
  background: inherit;
  animation: scrollLine 2s ease-in-out infinite;
}

.arrow-head {
  position: absolute;
  bottom: -5px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 8px solid var(--accent-color);
  animation: bounce 2s infinite;
}

/* Advanced Keyframe Animations */
@keyframes backgroundPulse {
  0% { opacity: 0.5; transform: scale(1); }
  100% { opacity: 0.8; transform: scale(1.05); }
}

@keyframes sparkle {
  0% { transform: translateX(0) translateY(0); }
  100% { transform: translateX(-100px) translateY(-50px); }
}

@keyframes overlayShift {
  0% { background-position: 0% 50%; }
  100% { background-position: 100% 50%; }
}

@keyframes contentFadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInLeft {
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(-10deg); }
  20% { transform: rotate(12deg); }
  40% { transform: rotate(-4deg); }
  50% { transform: rotate(10deg); }
  60% { transform: rotate(-6deg); }
  70% { transform: rotate(8deg); }
  80% { transform: rotate(-4deg); }
  90% { transform: rotate(4deg); }
}

@keyframes underlineExpand {
  to { width: 100%; }
}

@keyframes gradientShift {
  0% { background-position: 0% 50%; }
  100% { background-position: 100% 50%; }
}

@keyframes fadeInBounce {
  0% {
    opacity: 0;
    transform: translateY(20px) scale(0.8);
  }
  60% {
    opacity: 1;
    transform: translateY(-5px) scale(1.05);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes arrowSlide {
  to { opacity: 1; }
}

@keyframes lineSlideIn {
  to { opacity: 1; }
}

@keyframes typingCursor {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

@keyframes textReveal {
  to { width: 100%; }
}

@keyframes buttonPop {
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes visualSlideIn {
  to {
    opacity: 1;
    transform: translateX(0) scale(1);
  }
}

@keyframes rotateGlow {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes shimmer {
  0% { opacity: 0.3; }
  100% { opacity: 0.7; }
}

@keyframes imagePulse {
  0% { 
    box-shadow: 
      0 0 30px var(--shadow-glow),
      inset 0 0 20px rgba(125, 211, 252, 0.1);
  }
  100% { 
    box-shadow: 
      0 0 50px var(--shadow-glow),
      inset 0 0 30px rgba(125, 211, 252, 0.2);
  }
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateX(-50%) translateY(20px);
  }
  100% {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }
}

@keyframes scrollLine {
  0%, 100% {
    background: linear-gradient(to bottom, transparent, var(--accent-color), transparent);
  }
  50% {
    background: linear-gradient(to bottom, var(--accent-color), transparent, var(--accent-color));
  }
}

@keyframes bounce {
  0%, 100% { transform: translateX(-50%) translateY(0); }
  50% { transform: translateX(-50%) translateY(10px); }
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-15px); }
}

/* Vue Transition Classes - Enhanced */
.fade-slide-down-enter-active { 
  transition: all 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94); 
}
.fade-slide-down-enter-from { 
  opacity: 0; 
  transform: translateY(-80px) scale(0.9); 
}

.fade-slide-up-enter-active { 
  transition: all 1.2s cubic-bezier(0.25, 0.46, 0.45, 0.94); 
  transition-delay: 0.4s;
}
.fade-slide-up-enter-from { 
  opacity: 0; 
  transform: translateY(80px) scale(0.9) rotateX(15deg); 
}

.fade-up-enter-active { 
  transition: all 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94); 
  transition-delay: 0.8s;
}
.fade-up-enter-from { 
  opacity: 0; 
  transform: translateY(30px) scale(0.95); 
}

/* Icon Styles with Animations */
.icon-download::before { 
  content: '📥'; 
  margin-right: 0.5rem; 
  display: inline-block;
  animation: iconBounce 2s ease-in-out infinite;
}
.icon-eye::before { 
  content: '👁️'; 
  margin-right: 0.5rem;
  display: inline-block;
  animation: iconPulse 1.5s ease-in-out infinite alternate;
}

@keyframes iconBounce {
  0%, 100% { transform: scale(1); }
  50% { transform: scale(1.2); }
}

@keyframes iconPulse {
  0% { opacity: 0.7; }
  100% { opacity: 1; }
}

/* Responsive Design */
@media (max-width: 1024px) {
  .hero-layout {
    gap: 3rem;
  }
  
  .hero-img-container {
    width: 300px;
    height: 300px;
  }
}

@media (max-width: 768px) {
  .hero-layout {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }
  
  .hero-text {
    order: 2;
  }
  
  .hero-text > * {
    transform: translateY(30px);
    animation-name: slideInUp;
  }
  
  .hero-visual {
    order: 1;
    transform: translateY(30px) scale(0.8);
    animation-name: slideInDown;
            margin-top: 2rem;
  }
  
  .hero-img-container {
    width: 250px;
    height: 250px;
  }
  
  .hero-actions {
    justify-content: center;
  }
  
  .hero-subtitle::before {
    display: none;
  }
}

@keyframes slideInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes slideInDown {
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@media (max-width: 480px) {
  .container {
    padding: 0 1rem;
    margin-top: 2rem;
  }
  
  .hero-actions {
    flex-direction: column;
    align-items: center;
  }
  
  .btn {
    width: 80%;
    justify-content: center;
  }
  
  .hero-img-container {
    width: 200px;
    height: 200px;
  }
}
</style>