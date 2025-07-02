<template>
  <footer class="footer-bar">
    <div class="footer-content">
      <div class="contact-info">
        <span class="phone">📞Whats App 03232978278</span>
      </div>
      <div class="socials">
        <a v-for="icon in socials" :key="icon.link" :href="icon.link" target="_blank" :title="icon.name" class="social-icon">
          <i :class="icon.icon"></i>
        </a>
      </div>
      <div class="copyright">
        &copy; {{ new Date().getFullYear() }} Z. Developer. All rights reserved.
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "FooterBar",
  data() {
    return {
      socials: [
        { name: "GitHub", icon: "fab fa-github", link: "https://github.com/yourusername" },
        { name: "LinkedIn", icon: "fab fa-linkedin", link: "https://www.linkedin.com/feed/" },
        { name: "Twitter", icon: "fab fa-twitter", link: "https://x.com/WebZubair" },
      ],
    };
  },
};
</script>

<style scoped>
.footer-bar {
  background: #18181b;
  color: #e0e0e6;
  padding: 1.7rem 0 1.1rem 0;
  box-shadow: 0 -2px 18px #09090b77;
}
.footer-content {
  width: 95vw;
  max-width: 1000px;
  margin: 0 auto;
  text-align: center;
}
.phone {
  color: #7dd3fc;
  font-size: 1.08rem;
  font-weight: 600;
  letter-spacing: 1.5px;
}
.socials {
  margin: 1.1rem 0 0.7rem 0;
  display: flex;
  justify-content: center;
  gap: 1.7rem;
}
.social-icon {
  color: #7dd3fc;
  font-size: 1.3rem;
  background: #23232a;
  border-radius: 50%;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 2.65rem;
  height: 2.65rem;
  transition: background 0.22s, box-shadow 0.22s, transform 0.18s;
  box-shadow: 0 1.5px 5px #2563eb55;
}
.social-icon:hover {
  background: #0ea5e9;
  color: #fff;
  transform: scale(1.09) rotate(-6deg);
}
.copyright {
  color: #b4b4c0;
  font-size: 0.97rem;
  margin-top: 0.85rem;
  letter-spacing: 0.5px;
}
</style>