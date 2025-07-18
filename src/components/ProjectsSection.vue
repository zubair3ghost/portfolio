



<template>
  <section class="portfolio-section">
    <div class="container">
      <div class="section-header">
        <h1>My Work</h1>
        <p class="section-subtitle">
          A showcase of my recent work and creative projects
        </p>
      </div>

      <div class="projects-grid">
        <div
          v-for="project in projects"
          :key="project.id"
          class="project-card"
          @click="openProject(project)"
        >
          <div class="card-image">
            <img :src="project.image" :alt="project.title" />
            <div class="image-overlay">
              <div class="overlay-content">
                <button class="view-btn">
                  <i class="icon-eye"></i>
                  View Project
                </button>
              </div>
            </div>
          </div>

          <div class="card-content">
            <div class="card-header">
              <h3 class="project-title">{{ project.title }}</h3>
              <span class="project-category">{{ project.category }}</span>
            </div>

            <p class="project-description">{{ project.description }}</p>

            <div class="project-tech">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="tech-tag"
              >
                {{ tech }}
              </span>
            </div>

            <div class="card-footer">
              <div class="project-links">
                <a
                  v-if="project.liveUrl"
                  :href="project.liveUrl"
                  target="_blank"
                  class="project-link live"
                  @click.stop
                >
                  <i class="icon-external"></i>
                  Live Demo
                </a>
                <a
                  v-if="project.githubUrl"
                  :href="project.githubUrl"
                  target="_blank"
                  class="project-link github"
                  @click.stop
                >
                  <i class="icon-github"></i>
                  GitHub
                </a>
              </div>
              <div class="project-date">{{ project.date }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'PortfolioProjects',
  data() {
    return {
      projects: [
        {
          id: 1,
          title: 'E-Commerce Platform',
          category: 'Web Development',
          description: 'A full-stack e-commerce solution with payment integration, user authentication, and admin dashboard.',
          image: 'https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?w=600&h=400&fit=crop',
          technologies: ['Vue.js', 'Node.js', 'MongoDB', 'Stripe'],
          liveUrl: 'https://example.com',
          githubUrl: 'https://github.com/username/project',
          date: '2024'
        },
        {
          id: 2,
          title: 'Task Management App',
          category: 'Mobile App',
          description: 'A cross-platform mobile app for task management with real-time collaboration features.',
          image: 'https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=600&h=400&fit=crop',
          technologies: ['React Native', 'Firebase', 'Redux'],
          liveUrl: 'https://example.com',
          githubUrl: 'https://github.com/username/project',
          date: '2024'
        },
        {
          id: 3,
          title: 'Weather Dashboard',
          category: 'Web Development',
          description: 'A responsive weather dashboard with interactive charts and location-based forecasts.',
          image: 'https://images.unsplash.com/photo-1504608524841-42fe6f032b4b?w=600&h=400&fit=crop',
          technologies: ['React', 'Chart.js', 'OpenWeather API'],
          liveUrl: 'https://example.com',
          githubUrl: 'https://github.com/username/project',
          date: '2023'
        },
        {
          id: 4,
          title: 'AI Image Generator',
          category: 'AI/ML',
          description: 'An AI-powered image generation tool using machine learning models and modern web technologies.',
          image: 'https://images.unsplash.com/photo-1677442136019-21780ecad995?w=600&h=400&fit=crop',
          technologies: ['Python', 'TensorFlow', 'FastAPI', 'Vue.js'],
          liveUrl: 'https://example.com',
          githubUrl: 'https://github.com/username/project',
          date: '2023'
        },
        {
          id: 5,
          title: 'Portfolio Website',
          category: 'Web Design',
          description: 'A modern, responsive portfolio website with smooth animations and interactive elements.',
          image: 'https://images.unsplash.com/photo-1467232004584-a241de8bcf5d?w=600&h=400&fit=crop',
          technologies: ['Vue.js', 'SCSS', 'GSAP'],
          liveUrl: 'https://example.com',
          githubUrl: 'https://github.com/username/project',
          date: '2023'
        },
        {
          id: 6,
          title: 'Crypto Tracker',
          category: 'Web Development',
          description: 'A real-time cryptocurrency tracking application with portfolio management features.',
          image: 'https://images.unsplash.com/photo-1640340434855-6084b1f4901c?w=600&h=400&fit=crop',
          technologies: ['Next.js', 'TypeScript', 'CoinGecko API'],
          liveUrl: 'https://example.com',
          githubUrl: 'https://github.com/username/project',
          date: '2023'
        }
      ]
    }
  },
  methods: {
    openProject(project) {
      // Handle project click - could open modal, navigate to detail page, etc.
      console.log('Opening project:', project.title);
      // You can emit an event or use router navigation here
      this.$emit('project-selected', project);
    }
  }
}
</script>

<style scoped>
/* CSS Variables for easy customization */
:root {
  --primary-bg: #0f0f0f;
  --secondary-bg: #1a1a1a;
  --card-bg: #262626;
  --text-primary: #ffffff;
  --text-secondary: #a3a3a3;
  --text-muted: #737373;
  --accent-color: #60a5fa;
  --accent-hover: #3b82f6;
  --border-color: rgba(255, 255, 255, 0.1);
  --shadow-light: rgba(255, 255, 255, 0.05);
  --shadow-dark: rgba(0, 0, 0, 0.3);
}

/* Main Styles */
.portfolio-section {
  min-height: 100vh;
  background: linear-gradient(135deg, var(--primary-bg) 0%, var(--secondary-bg) 100%);
  padding: 4rem 0;
  font-family: 'Inter', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-size: 3rem;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 1rem;
  background: linear-gradient(135deg, var(--text-primary), var(--text-secondary));
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  transition: all 0.3s ease;
}

.section-subtitle {
  font-size: 1.2rem;
  color: var(--text-secondary);
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  align-items: start;
}

.project-card {
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(10px);
  border: 1px solid var(--border-color);
  border-radius: 16px;
  overflow: hidden;
  cursor: pointer;
  transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  position: relative;
  animation: fadeInUp 0.6s ease-out;
  animation-fill-mode: both;
}

.project-card:hover {
  transform: translateY(-8px) scale(1.02);
  box-shadow: 0 20px 40px var(--shadow-dark);
  border-color: rgba(96, 165, 250, 0.3);
}

.project-card:hover .image-overlay {
  opacity: 1;
}

.project-card:hover .project-title {
  color: var(--accent-color);
}

.project-card:active {
  transform: translateY(-4px) scale(1.01);
}

.card-image {
  position: relative;
  height: 220px;
  overflow: hidden;
}

.card-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(96, 165, 250, 0.8), rgba(59, 130, 246, 0.9));
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: all 0.3s ease;
}

.overlay-content {
  text-align: center;
}

.view-btn {
  background: rgba(255, 255, 255, 0.2);
  border: 2px solid rgba(255, 255, 255, 0.3);
  color: var(--text-primary);
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  font-weight: 600;
  transition: all 0.3s ease;
  cursor: pointer;
}

.view-btn:hover {
  background: rgba(255, 255, 255, 0.3);
  transform: translateY(-2px);
}

.icon-eye::before {
  content: '👁';
  margin-right: 0.5rem;
}

.card-content {
  padding: 1.5rem;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
  gap: 1rem;
}

.project-title {
  font-size: 1.4rem;
  font-weight: 700;
  color: var(--text-primary);
  transition: all 0.3s ease;
  flex: 1;
}

.project-category {
  background: linear-gradient(135deg, var(--accent-color), var(--accent-hover));
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 600;
  white-space: nowrap;
}

.project-description {
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 1rem;
  font-size: 0.95rem;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-tag {
  background: rgba(255, 255, 255, 0.08);
  color: var(--text-secondary);
  padding: 0.3rem 0.75rem;
  border-radius: 6px;
  font-size: 0.8rem;
  font-weight: 500;
  border: 1px solid var(--border-color);
  transition: all 0.3s ease;
}

.tech-tag:hover {
  background: rgba(96, 165, 250, 0.2);
  color: var(--accent-color);
  border-color: rgba(96, 165, 250, 0.3);
}

.card-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.project-links {
  display: flex;
  gap: 0.75rem;
}

.project-link {
  color: var(--text-secondary);
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
  transition: all 0.3s ease;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  border: 1px solid var(--border-color);
}

.project-link:hover {
  color: var(--accent-color);
  border-color: rgba(96, 165, 250, 0.5);
  background: rgba(96, 165, 250, 0.1);
}

.project-link.live .icon-external::before {
  content: '🔗';
  margin-right: 0.5rem;
}

.project-link.github .icon-github::before {
  content: '⚡';
  margin-right: 0.5rem;
}

.project-date {
  color: var(--text-muted);
  font-size: 0.85rem;
  font-weight: 500;
}

/* Responsive Design */
@media (max-width: 768px) {
  .portfolio-section {
    padding: 2rem 0;
  }

  .container {
    padding: 0 1rem;
  }

  .section-header {
    margin-bottom: 2rem;
  }

  .section-title {
    font-size: 2.5rem;
  }

  .section-subtitle {
    font-size: 1.1rem;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .project-card:hover {
    transform: translateY(-4px) scale(1.01);
  }

  .card-image {
    height: 180px;
  }

  .card-content {
    padding: 1.25rem;
  }

  .card-header {
    flex-direction: column;
    align-items: flex-start;
    gap: 0.75rem;
  }

  .project-category {
    align-self: flex-start;
  }

  .card-footer {
    flex-direction: column;
    align-items: flex-start;
    gap: 1rem;
  }

  .project-links {
    order: 2;
  }

  .project-date {
    order: 1;
    align-self: flex-end;
  }
}

@media (max-width: 480px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }

  .section-title {
    font-size: 2rem;
  }

  .card-content {
    padding: 1rem;
  }

  .project-links {
    flex-direction: column;
    width: 100%;
  }

  .project-link {
    text-align: center;
    justify-content: center;
  }
}

/* Animation keyframes */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Staggered animation delays */
.project-card:nth-child(1) { animation-delay: 0s; }
.project-card:nth-child(2) { animation-delay: 0.1s; }
.project-card:nth-child(3) { animation-delay: 0.2s; }
.project-card:nth-child(4) { animation-delay: 0.3s; }
.project-card:nth-child(5) { animation-delay: 0.4s; }
.project-card:nth-child(6) { animation-delay: 0.5s; }
</style>