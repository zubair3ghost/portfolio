<template>
  <div class="services-container">
    <div class="services-header">
      <h1 class="main-title">My Services</h1>
      <p class="subtitle">Transforming ideas into powerful digital solutions</p>
    </div>
    
    <div class="services-grid">
      <div 
        v-for="(service, index) in services" 
        :key="index"
        class="service-card"
        :style="{ animationDelay: `${index * 0.1}s` }"
        @mouseenter="hoveredCard = index"
        @mouseleave="hoveredCard = null"
      >
        <div class="icon-wrapper">
          <span class="icon" v-html="service.icon"></span>
        </div>
        <h3 class="service-title">{{ service.title }}</h3>
        <p class="service-description">{{ service.description }}</p>
        <div class="service-features">
          <span 
            v-for="(feature, idx) in service.features" 
            :key="idx"
            class="feature-tag"
          >
            {{ feature }}
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ServicesSection',
  data() {
    return {
      hoveredCard: null,
      services: [
        {
          icon: '🎨',
          title: 'Frontend Development',
          description: 'Creating stunning, responsive and interactive user interfaces with modern frameworks and best practices.',
          features: ['Angular', 'Vue.js','React', 'Tailwind CSS', 'Responsive Design']
        },
        {
          icon: '⚙️',
          title: 'Backend Development',
          description: 'Building robust, scalable server-side applications with secure APIs and efficient database management.',
          features: ['Node.js', 'Express','NestJS', 'MongoDB', 'PostgreSQL']
        },
        {
          icon: '🚀',
          title: 'Full Stack Applications',
          description: 'End-to-end development of complete web applications from concept to deployment and maintenance.',
          features: ['MEAN Stack', 'MERN Stack','MEVN Stack','RESTful APIs', 'Authentication', 'Deployment']
        },
        {
          icon: '🛒',
          title: 'E-Commerce Solutions',
          description: 'Custom online stores with payment integration, inventory management, and seamless shopping experience.',
          features: ['Shopping Cart', 'Payment Gateway', 'Admin Panel', 'Analytics']
        },
        {
          icon: '📱',
          title: 'Web Applications',
          description: 'Dynamic and feature-rich web apps tailored to your business needs with real-time functionality.',
          features: ['Real-time Updates', 'Progressive Web Apps', 'Cloud Integration', 'API Development']
        },
        {
          icon: '🔧',
          title: 'Website Maintenance',
          description: 'Ongoing support, updates, bug fixes, and performance optimization to keep your site running smoothly.',
          features: ['Bug Fixes', 'Updates', 'Performance', 'Security']
        }
      ]
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

.services-container {
  background-color: #000;
  min-height: 100vh;
  padding: 80px 20px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.services-header {
  text-align: center;
  margin-bottom: 60px;
  animation: fadeInDown 0.8s ease-out;
}

.main-title {
  font-size: 48px;
  font-weight: 700;
  color: #fff;
  margin-bottom: 15px;
  background:linear-gradient(135deg, #60a5fa, #3b82f6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle {
  font-size: 18px;
  color: #a0a0a0;
  font-weight: 300;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 30px;
  max-width: 1200px;
  margin: 0 auto;
}

.service-card {
  background: linear-gradient(145deg, #1a1a1a, #0d0d0d);
  border: 1px solid #2a2a2a;
  border-radius: 16px;
  padding: 35px 30px;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  cursor: pointer;
  position: relative;
  overflow: hidden;
  animation: fadeInUp 0.6s ease-out backwards;
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, #667eea30 0%, #764ba230 100%);
  opacity: 0;
  transition: opacity 0.4s ease;
  pointer-events: none;
}

.service-card:hover {
  transform: translateY(-10px);
  border-color: #667eea;
  box-shadow: 0 20px 40px rgba(102, 126, 234, 0.3);
}

.service-card:hover::before {
  opacity: 1;
}

.icon-wrapper {
  width: 70px;
  height: 70px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 25px;
  transition: transform 0.4s ease;
}

.service-card:hover .icon-wrapper {
  transform: rotate(360deg) scale(1.1);
}

.icon {
  font-size: 32px;
}

.service-title {
  font-size: 24px;
  font-weight: 600;
  color: #fff;
  margin-bottom: 15px;
  transition: color 0.3s ease;
}

.service-card:hover .service-title {
  color: #667eea;
}

.service-description {
  font-size: 15px;
  line-height: 1.7;
  color: #b0b0b0;
  margin-bottom: 20px;
}

.service-features {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.feature-tag {
  background-color: #1a1a1a;
  border: 1px solid #333;
  color: #888;
  padding: 6px 14px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 500;
  transition: all 0.3s ease;
}

.service-card:hover .feature-tag {
  background-color: #667eea20;
  border-color: #667eea;
  color: #667eea;
}

@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

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

@media (max-width: 768px) {
  .services-container {
    padding: 60px 15px;
  }
  
  .main-title {
    font-size: 36px;
  }
  
  .services-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  
  .service-card {
    padding: 30px 25px;
  }
}
</style>