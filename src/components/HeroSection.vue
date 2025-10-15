<!-- 
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
                <a href="/resume.pdf" class="btn primary" download>
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
                  <img src="@/assets/zubair.jpg" alt="M. Developer" class="hero-img">
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
  z-index: 1;
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
  z-index: 1;
}

.img-frame {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
  border: 3px solid var(--accent-color);
  box-shadow: 0 4px 20px rgba(59, 130, 246, 0.4), 
            0 0 10px rgba(59, 130, 246, 0.2);
  /* box-shadow: 
    0 0 30px var(--shadow-glow),
    inset 0 0 20px rgba(125, 211, 252, 0.1); */
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
  box-shadow: 0 4px 20px rgba(59, 130, 246, 0.4), 
            0 0 10px rgba(59, 130, 246, 0.2);
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
</style> -->










<template>
  <section id="hero" class="hero-section">
    <!-- Animated Background -->
    <div class="hero-bg">
      <div class="grid-overlay"></div>
      <div class="gradient-orb orb-1"></div>
      <div class="gradient-orb orb-2"></div>
      <div class="gradient-orb orb-3"></div>
    </div>
    
    <div class="container">
      <div class="hero-content">
        <!-- Left Content -->
        <div class="hero-left">
          <div class="greeting-wrapper">
            <span class="wave-emoji">👋</span>
            <div class="greeting-text">
              <span class="greeting-label">Hello there!</span>
              <div class="tag-badge">
                <span class="dot"></span>
                Available for Freelance
              </div>
            </div>
          </div>
          
          <h1 class="hero-title">
            <span class="title-line">I'm <span class="highlight">Zubair Ahmad</span></span>
            <span class="title-role">Full Stack Web Developer</span>
            <span class="title-subtitle">{{ typedText }}<span class="cursor">|</span></span>
          </h1>
          
          <p class="hero-description">
            Transforming ideas into <strong>powerful digital solutions</strong>. I specialize in building 
            <strong>responsive, scalable web applications</strong> that drive business growth and deliver 
            exceptional user experiences. From concept to deployment, I bring your vision to life with 
            <strong>clean code</strong> and <strong>modern technologies</strong>.
          </p>
          
          <div class="hero-highlights">
            <div class="highlight-item">
              <svg class="check-icon" width="20" height="20" viewBox="0 0 20 20" fill="none">
                <path d="M16.667 5L7.5 14.167 3.333 10" stroke="#00D4FF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <span>100% Project Completion Rate</span>
            </div>
            <div class="highlight-item">
              <svg class="check-icon" width="20" height="20" viewBox="0 0 20 20" fill="none">
                <path d="M16.667 5L7.5 14.167 3.333 10" stroke="#00D4FF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <span>Fast Turnaround & Quality Delivery</span>
            </div>
            <div class="highlight-item">
              <svg class="check-icon" width="20" height="20" viewBox="0 0 20 20" fill="none">
                <path d="M16.667 5L7.5 14.167 3.333 10" stroke="#00D4FF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <span>Ongoing Support & Maintenance</span>
            </div>
          </div>
          
          <!-- <div class="hero-stats">
            <div class="stat-item">
              <span class="stat-number">5+</span>
              <span class="stat-label">Years Experience</span>
            </div>
            <div class="stat-divider"></div>
            <div class="stat-item">
              <span class="stat-number">50+</span>
              <span class="stat-label">Projects Completed</span>
            </div>
            <div class="stat-divider"></div>
            <div class="stat-item">
              <span class="stat-number">98%</span>
              <span class="stat-label">Client Satisfaction</span>
            </div>
          </div> -->
          
          <div class="hero-actions">
            <a href="#contact" class="btn btn-primary">
              <span class="btn-text">Hire Me Now</span>
              <svg class="btn-icon" width="20" height="20" viewBox="0 0 20 20" fill="none">
                <path d="M7 3L14 10L7 17" stroke="currentColor" stroke-width="2" stroke-linecap="round"/>
              </svg>
            </a>
             <a href="/resume.pdf" class="btn btn-secondary" download>
                  <i class="icon-download"></i>
                  Download Resume
                </a>
            <!-- <a href="#projects" class="btn btn-secondary">
              <span class="btn-text">View Portfolio</span>
            </a> -->
          </div>
          
          <div class="social-proof">
            <div class="client-avatars">
              <div class="avatar"></div>
              <div class="avatar"></div>
              <div class="avatar"></div>
              <div class="avatar-more">+30</div>
            </div>
            <div class="social-proof-text">
              <strong>Trusted by clients</strong>
              <span>worldwide for quality web solutions</span>
            </div>
          </div>
        </div>
        
        <!-- Right Content - Profile Image -->
        <div class="hero-right">
          <div class="profile-container">
            <div class="profile-glow"></div>
            <div class="profile-ring"></div>
            <div class="profile-image">
              <img src="@/assets/zubair.jpg" alt="Muhammad Zubair - Full Stack Developer" />
            </div>
            <div class="floating-badge badge-1">
              <span class="badge-icon">💼</span>
              <div class="badge-content">
                <span class="badge-title">Professional</span>
                <span class="badge-subtitle">Developer</span>
              </div>
            </div>
            <div class="floating-badge badge-2">
              <span class="badge-icon">⚡</span>
              <div class="badge-content">
                <span class="badge-title">Fast</span>
                <span class="badge-subtitle">Delivery</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Scroll Indicator -->
      <div class="scroll-indicator">
        <span class="scroll-text">Scroll to explore</span>
        <div class="scroll-line"></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ProfessionalHero',
  data() {
    return {
      texts: [
        'Crafting Modern Web Experiences',
        'Building Scalable Applications',
        'Turning Ideas Into Reality',
        'Your Partner in Digital Success'
      ],
      typedText: '',
      textIndex: 0,
      charIndex: 0,
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
      const currentText = this.texts[this.textIndex];
      
      if (this.isDeleting) {
        this.typedText = currentText.substring(0, this.charIndex - 1);
        this.charIndex--;
      } else {
        this.typedText = currentText.substring(0, this.charIndex + 1);
        this.charIndex++;
      }
      
      let speed = this.isDeleting ? this.deleteSpeed : this.typeSpeed;
      
      if (!this.isDeleting && this.charIndex === currentText.length) {
        speed = this.pauseTime;
        this.isDeleting = true;
      } else if (this.isDeleting && this.charIndex === 0) {
        this.isDeleting = false;
        this.textIndex = (this.textIndex + 1) % this.texts.length;
      }
      
      setTimeout(() => this.typeText(), speed);
    }
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.hero-section {
  position: relative;
  min-height: 100vh;
  background: #000000;
  overflow: hidden;
  display: flex;
  align-items: center;
  padding: 80px 0 40px;
}

/* Animated Background */
.hero-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.grid-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: 
    linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: gridMove 20s linear infinite;
}

.gradient-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.4;
  animation: float 8s ease-in-out infinite;
}

.orb-1 {
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, #00D4FF 0%, transparent 70%);
  top: -100px;
  left: -100px;
  animation-delay: 0s;
}

.orb-2 {
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, #667eea 0%, transparent 70%);
  bottom: -150px;
  right: -150px;
  animation-delay: 2s;
}

.orb-3 {
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, #764ba2 0%, transparent 70%);
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  animation-delay: 4s;
}

.container {
  position: relative;
  z-index: 2;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 40px;
  width: 100%;
}

.hero-content {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 60px;
  align-items: center;
}

/* Left Content */
.hero-left {
  animation: slideInLeft 1s ease-out;
}

.greeting-wrapper {
  display: flex;
  align-items: center;
  gap: 15px;
  margin-bottom: 30px;
  animation: fadeIn 1s ease-out 0.2s both;
}

.wave-emoji {
  font-size: 40px;
  animation: wave 2s ease-in-out infinite;
  transform-origin: 70% 70%;
}

.greeting-text {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.greeting-label {
  font-size: 16px;
  color: #a0a0a0;
  font-weight: 500;
}

.tag-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 16px;
  background: rgba(0, 212, 255, 0.1);
  border: 1px solid rgba(0, 212, 255, 0.3);
  border-radius: 50px;
  font-size: 13px;
  color: #00D4FF;
  font-weight: 600;
  width: fit-content;
}

.dot {
  width: 8px;
  height: 8px;
  background: #00D4FF;
  border-radius: 50%;
  animation: pulse 2s ease-in-out infinite;
}

.hero-title {
  margin-bottom: 25px;
  animation: fadeIn 1s ease-out 0.4s both;
}

.title-line {
  display: block;
  font-size: 24px;
  color: #ffffff;
  font-weight: 400;
  margin-bottom: 10px;
}

.highlight {
  color: #00D4FF;
  font-weight: 700;
}

.title-role {
  display: block;
  font-size: 56px;
  font-weight: 800;
  background: linear-gradient(135deg, #ffffff 0%, #00D4FF 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 15px;
  line-height: 1.1;
}

.title-subtitle {
  display: block;
  font-size: 20px;
  color: #00D4FF;
  font-weight: 500;
  margin-top: 10px;
  min-height: 30px;
}

.cursor {
  animation: blink 1s infinite;
  color: #00D4FF;
  font-weight: 300;
}

.hero-description {
  font-size: 17px;
  line-height: 1.8;
  color: #b0b0b0;
  margin-bottom: 30px;
  animation: fadeIn 1s ease-out 0.6s both;
}

.hero-description strong {
  color: #ffffff;
  font-weight: 600;
}

.hero-highlights {
  display: flex;
  flex-direction: column;
  gap: 12px;
  margin-bottom: 35px;
  animation: fadeIn 1s ease-out 0.8s both;
}

.highlight-item {
  display: flex;
  align-items: center;
  gap: 12px;
  color: #e0e0e0;
  font-size: 15px;
}

.check-icon {
  flex-shrink: 0;
}

.hero-stats {
  display: flex;
  align-items: center;
  gap: 30px;
  padding: 25px 0;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  margin-bottom: 35px;
  animation: fadeIn 1s ease-out 1s both;
}

.stat-item {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.stat-number {
  font-size: 36px;
  font-weight: 800;
  color: #00D4FF;
  line-height: 1;
}

.stat-label {
  font-size: 13px;
  color: #808080;
  font-weight: 500;
}

.stat-divider {
  width: 1px;
  height: 40px;
  background: rgba(255, 255, 255, 0.1);
}

.hero-actions {
  display: flex;
  gap: 15px;
  margin-bottom: 40px;
  animation: fadeIn 1s ease-out 1.2s both;
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 16px 32px;
  border-radius: 50px;
  font-size: 16px;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.3s ease-out;
  position: relative;
  overflow: hidden;
  cursor: pointer;
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
  transition: width 0.6s ease, height 0.6s ease;
}

.btn:hover::before {
  width: 300px;
  height: 300px;
}

.btn-primary {
  background: linear-gradient(135deg, #00D4FF 0%, #0ea5e9 100%);
  color: #000000;
  border: none;
  box-shadow: 0 4px 20px rgba(0, 212, 255, 0.4);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 30px rgba(0, 212, 255, 0.6);
}

.btn-secondary {
  background: transparent;
  color: #ffffff;
  border: 2px solid rgba(255, 255, 255, 0.2);
}

.btn-secondary:hover {
  border-color: #00D4FF;
  color: #00D4FF;
  background: rgba(0, 212, 255, 0.1);
}

.btn-text {
  position: relative;
  z-index: 1;
}

.btn-icon {
  position: relative;
  z-index: 1;
  transition: transform 0.3s ease;
}

.btn:hover .btn-icon {
  transform: translateX(5px);
}

.social-proof {
  display: flex;
  align-items: center;
  gap: 20px;
  animation: fadeIn 1s ease-out 1.4s both;
}

.client-avatars {
  display: flex;
  align-items: center;
}

.avatar {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  border: 3px solid #000000;
  background: linear-gradient(135deg, #667eea, #764ba2);
  margin-left: -15px;
}

.avatar:first-child {
  margin-left: 0;
}

.avatar-more {
  width: 45px;
  height: 45px;
  border-radius: 50%;
  border: 3px solid #000000;
  background: rgba(0, 212, 255, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 13px;
  color: #00D4FF;
  font-weight: 700;
  margin-left: -15px;
}

.social-proof-text {
  display: flex;
  flex-direction: column;
  gap: 3px;
}

.social-proof-text strong {
  font-size: 15px;
  color: #ffffff;
  font-weight: 600;
}

.social-proof-text span {
  font-size: 13px;
  color: #808080;
}

/* Right Content - Profile */
.hero-right {
  display: flex;
  justify-content: center;
  align-items: center;
  animation: slideInRight 1s ease-out;
}

.profile-container {
  position: relative;
  width: 400px;
  height: 400px;
}

.profile-glow {
  position: absolute;
  top: -20px;
  left: -20px;
  right: -20px;
  bottom: -20px;
  background: radial-gradient(circle, rgba(0, 212, 255, 0.4) 0%, transparent 70%);
  border-radius: 50%;
  animation: glowPulse 3s ease-in-out infinite;
  z-index: 1;
}

.profile-ring {
  position: absolute;
  top: -10px;
  left: -10px;
  right: -10px;
  bottom: -10px;
  border: 3px solid transparent;
  border-radius: 50%;
  background: linear-gradient(45deg, #00D4FF, #667eea, #764ba2, #00D4FF) border-box;
  -webkit-mask: linear-gradient(#fff 0 0) padding-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  animation: rotate 4s linear infinite;
  z-index: 2;
}

.profile-image {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 50%;
  overflow: hidden;
  z-index: 3;
  border: 5px solid #000000;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
}

.profile-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.floating-badge {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 12px 20px;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 50px;
  z-index: 4;
  animation: float 3s ease-in-out infinite;
}

.badge-1 {
  top: 20px;
  right: -20px;
  animation-delay: 0s;
}

.badge-2 {
  bottom: 40px;
  left: -20px;
  animation-delay: 1.5s;
}

.badge-icon {
  font-size: 24px;
}

.badge-content {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.badge-title {
  font-size: 14px;
  color: #00D4FF;
  font-weight: 700;
}

.badge-subtitle {
  font-size: 12px;
  color: #808080;
}

/* Scroll Indicator */
.scroll-indicator {
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  animation: fadeIn 1s ease-out 1.6s both;
}

.scroll-text {
  font-size: 12px;
  color: #808080;
  text-transform: uppercase;
  letter-spacing: 2px;
}

.scroll-line {
  width: 2px;
  height: 50px;
  background: linear-gradient(to bottom, #00D4FF, transparent);
  position: relative;
  animation: scrollMove 2s ease-in-out infinite;
}

/* Animations */
@keyframes gridMove {
  0% { transform: translate(0, 0); }
  100% { transform: translate(50px, 50px); }
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-20px); }
}

@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(-10deg); }
  20% { transform: rotate(12deg); }
  40% { transform: rotate(-4deg); }
  50% { transform: rotate(10deg); }
}

@keyframes pulse {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(0.8); }
}

@keyframes blink {
  0%, 50% { opacity: 1; }
  51%, 100% { opacity: 0; }
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes glowPulse {
  0%, 100% { opacity: 0.4; transform: scale(1); }
  50% { opacity: 0.6; transform: scale(1.1); }
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

@keyframes scrollMove {
  0% { opacity: 0; transform: translateY(-20px); }
  50% { opacity: 1; }
  100% { opacity: 0; transform: translateY(20px); }
}

/* Responsive Design */
@media (max-width: 1024px) {
  .hero-content {
    grid-template-columns: 1fr;
    gap: 60px;
    text-align: center;
  }
  
  .hero-left {
    order: 2;
  }
  
  .hero-right {
    order: 1;
  }
  
  .greeting-wrapper {
    justify-content: center;
  }
  
  .hero-highlights,
  .hero-stats,
  .hero-actions,
  .social-proof {
    justify-content: center;
  }
  
  .profile-container {
    width: 350px;
    height: 350px;
  }
}

@media (max-width: 768px) {
  .container {
    padding: 0 20px;
  }
  
  .title-role {
    font-size: 40px;
  }
  
  .hero-stats {
    flex-wrap: wrap;
    gap: 20px;
  }
  
  .stat-divider {
    display: none;
  }
  
  .hero-actions {
    flex-direction: column;
    width: 100%;
  }
  
  .btn {
    width: 100%;
    justify-content: center;
  }
  
  .profile-container {
    width: 280px;
    height: 280px;
  }
  
  .floating-badge {
    padding: 10px 15px;
  }
  
  .badge-1 {
    right: -10px;
  }
  
  .badge-2 {
    left: -10px;
  }
}

@media (max-width: 480px) {
  .title-role {
    font-size: 32px;
  }
  
  .hero-description {
    font-size: 15px;
  }
  
  .profile-container {
    width: 240px;
    height: 240px;
  }
}
</style>