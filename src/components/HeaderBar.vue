<template>
  <header class="site-header">
    <div class="container">
      <div class="logo">
        <a href="#hero">
          <img src="../assets/z.png" alt="">
        </a>
      </div>
      <nav class="desktop-nav">
        <a
          v-for="item in navItems"
          :key="item.href"
          :href="item.href"
          @click="closeMobileMenu"
        >{{ item.label }}</a>
      </nav>
      <!-- Burger/Cross Icon -->
      <button
        class="burger"
        :aria-label="mobileMenuOpen ? 'Close menu' : 'Open menu'"
        @click="toggleMobileMenu"
        :aria-expanded="mobileMenuOpen ? 'true' : 'false'"
      >
        <span v-if="!mobileMenuOpen" class="burger-lines">
          <span></span>
          <span></span>
          <span></span>
        </span>
        <span v-else class="cross-icon" aria-label="Close menu">
          <!-- A simple SVG cross icon -->
          <svg width="30" height="30" viewBox="0 0 30 30">
            <line x1="7" y1="7" x2="23" y2="23" stroke="#7dd3fc" stroke-width="3" stroke-linecap="round"/>
            <line x1="23" y1="7" x2="7" y2="23" stroke="#7dd3fc" stroke-width="3" stroke-linecap="round"/>
          </svg>
        </span>
      </button>
      <!-- Mobile Menu Overlay -->
      <transition name="slide-fade">
        <div
          v-if="mobileMenuOpen"
          class="mobile-menu-overlay"
          @click.self="closeMobileMenu"
        >
          <nav class="mobile-nav" @click.stop>
            <a
              v-for="item in navItems"
              :key="item.href"
              :href="item.href"
              @click="handleMobileNavClick"
            >{{ item.label }}</a>
          </nav>
        </div>
      </transition>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      navItems: [
        { label: "Home", href: "#hero" },
        { label: "Skills", href: "#skills" },
        { label: "Projects", href: "#projects" },
        { label: "Contact", href: "#contact" },
      ],
      mobileMenuOpen: false,
    };
  },
  mounted() {
    document.addEventListener("keydown", this.onKeydown);
    window.addEventListener("resize", this.onWindowResize);
  },
  beforeDestroy() {
    document.removeEventListener("keydown", this.onKeydown);
    window.removeEventListener("resize", this.onWindowResize);
  },
  methods: {
    toggleMobileMenu() {
      this.mobileMenuOpen = !this.mobileMenuOpen;
      if (this.mobileMenuOpen) {
        document.body.style.overflow = "hidden";
      } else {
        document.body.style.overflow = "";
      }
    },
    closeMobileMenu() {
      this.mobileMenuOpen = false;
      document.body.style.overflow = "";
    },
    handleMobileNavClick() {
      this.closeMobileMenu();
    },
    onKeydown(e) {
      if (this.mobileMenuOpen && (e.key === "Escape" || e.key === "Esc")) {
        this.closeMobileMenu();
      }
    },
    onWindowResize() {
      if (window.innerWidth > 700 && this.mobileMenuOpen) {
        this.closeMobileMenu();
      }
    },
  },
};
</script>

<style scoped >
.site-header {
  width: 100%;
  background: #18181b;
  box-shadow: 0 2px 10px #0003;
  position: fixed;
  top: 0;
  left: 0;
  z-index: 40;
}
.container {
  max-width: 1120px;
  margin: 0 auto;
  padding: 0 2.2rem;
  display: flex;
  align-items: center;
  height: 64px;
  justify-content: space-between;
  position: relative;
}
.logo a {
  color: #7dd3fc;
  text-decoration: none;
  font-size: 1.48rem;
  font-weight: 700;
  letter-spacing: 1.2px;
  transition: color 0.2s;
}
.logo a:hover {
  color: #0ea5e9;
}
.logo a img{
      width: 195px;
  }
.desktop-nav {
  display: flex;
  gap: 1.7rem;
}
.desktop-nav a {
  color: #e6e6ea;
  text-decoration: none;
  font-size: 1.06rem;
  font-weight: 600;
  letter-spacing: 0.5px;
  padding: 0.2rem 0.6rem;
  border-radius: 6px;
  transition: background 0.15s, color 0.15s;


    transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  
  /* Initial border setup */
  border: 2px solid transparent;
  
  /* Add subtle shadow */
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
/* .desktop-nav a:hover,
.desktop-nav a:focus {
  background: #23232a;
  color: #7dd3fc;
      border: 2px solid #7dd3fc;
    border-radius: 20px;
} */





/* Main hover effect */
.desktop-nav a:hover,
.desktop-nav a:focus {
  background: rgba(35, 35, 42, 0.95);
  color: #7dd3fc;
  border: 2px solid #7dd3fc;
  border-radius: 20px;
  
  /* Enhanced shadow on hover */
  box-shadow: 
    0 8px 25px rgba(125, 211, 252, 0.2),
    0 0 0 1px rgba(125, 211, 252, 0.1),
    inset 0 1px 0 rgba(255, 255, 255, 0.1);
  
  /* Subtle scale and lift effect */
  transform: translateY(-2px) scale(1.05);
  
  /* Text glow effect */
  text-shadow: 0 0 8px rgba(125, 211, 252, 0.6);
}

/* Animate background sweep on hover */
.desktop-nav a:hover::before {
  left: 100%;
}

/* Animate radial glow on hover */
.desktop-nav a:hover::after {
  width: 100%;
  height: 100%;
}
























/* Burger/Cross icon styles */
.burger {
  display: none;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 44px;
  height: 44px;
  background: none;
  border: none;
  cursor: pointer;
  z-index: 60;
  position: relative;
  margin-left: 0.5rem;
}
.burger-lines {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.burger-lines span {
  display: block;
  width: 26px;
  height: 3.2px;
  background: #7dd3fc;
  border-radius: 4px;
  margin: 4px 0;
  transition: all 0.27s cubic-bezier(.77,0,.175,1);
}
.cross-icon {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 30px;
  height: 30px;
  /* You can add a little rotation for style if you wish */
  transition: transform 0.2s;
}
.cross-icon svg {
  display: block;
}

/* Mobile menu overlay */
.mobile-menu-overlay {
  position: fixed;
  inset: 0;
  background: rgba(24, 24, 32, 0.97);
  z-index: 59;
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  animation: fadeInMenuBg 0.3s;
}
@keyframes fadeInMenuBg {
  from { opacity: 0;}
  to { opacity: 1;}
}
.mobile-nav {
  min-width: 270px;
  max-width: 90vw;
  background: #23232a;
  border-radius: 0 22px 22px 0;
  box-shadow: 0 4px 32px #0008;
  padding: 2.2rem 2.5rem 2.2rem 1.7rem;
  margin-top: 0;
  margin-left: 0;
  display: flex;
  flex-direction: column;
  gap: 1.6rem;
  animation: slideInMenu 0.33s cubic-bezier(.55,1.5,.45,1);
  transition: min-width 0.25s cubic-bezier(.55,1.5,.45,1);
}
@keyframes slideInMenu {
  from { transform: translateX(-120%); }
  to { transform: none; }
}
.mobile-nav a {
  color: #e6e6ea;
  text-decoration: none;
  font-size: 1.19rem;
  font-weight: 700;
  letter-spacing: 1px;
  padding: 0.45rem 0.5rem;
  border-radius: 8px;
  transition: background 0.13s, color 0.13s;
}
.mobile-nav a:hover,
.mobile-nav a:focus {
  background: #7dd3fc22;
  color: #7dd3fc;
  outline: none;
}

/* Hide desktop nav, show burger at <= 700px */
@media (max-width: 700px) {
  .desktop-nav {
    display: none;
  }
  .burger {
    display: flex;
  }
}
/* Hide burger and mobile menu at >700px */
@media (min-width: 701px) {
  .mobile-menu-overlay {
    display: none !important;
  }
  .burger {
    display: none !important;
  }
}

/* Slide-fade transition for menu overlay */
.slide-fade-enter-active {
  animation: fadeInMenuBg 0.3s;
}
.slide-fade-leave-active {
  animation: fadeOutMenuBg 0.21s;
}
@keyframes fadeOutMenuBg {
  from { opacity: 1;}
  to { opacity: 0;}
}
</style>