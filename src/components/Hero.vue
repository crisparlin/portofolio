<template>
  <section id="home" class="hero">
    <div class="hero-content">
      <div class="hero-text">
        <div class="hero-badge">
          <i class="fas fa-code"></i>
          <span>Professional IT Solutions</span>
        </div>
        <h1 class="hero-title">
          Transform Your Business with <span class="highlight">Modern Technology</span>
        </h1>
        <h2 class="hero-subtitle">{{ title }}</h2>
        <p class="hero-description">{{ description }}</p>
        <div class="value-props">
          <div class="value-prop">
            <i class="fas fa-rocket"></i>
            <span>Boost Performance</span>
          </div>
          <div class="value-prop">
            <i class="fas fa-shield-alt"></i>
            <span>Secure Solutions</span>
          </div>
          <div class="value-prop">
            <i class="fas fa-chart-line"></i>
            <span>Scale Your Business</span>
          </div>
        </div>
        <div class="hero-buttons">
          <button class="btn btn-primary" @click="scrollTo('contact')">
            <i class="fas fa-phone"></i>
            Get Free Consultation
          </button>
          <button class="btn btn-secondary" @click="scrollTo('portfolio')">
            <i class="fas fa-eye"></i>
            View Success Stories
          </button>
        </div>
        <div class="trust-indicators">
          <div class="trust-item">
            <strong>50+</strong>
            <span>Projects Delivered</span>
          </div>
          <div class="trust-item">
            <strong>99%</strong>
            <span>Client Satisfaction</span>
          </div>
          <div class="trust-item">
            <strong>24/7</strong>
            <span>Support Available</span>
          </div>
        </div>
      </div>
      <div class="hero-image">
        <div class="tech-showcase">
          <div class="tech-grid">
            <div class="tech-item">
              <i class="fab fa-vuejs"></i>
              <span>Vue.js</span>
            </div>
            <div class="tech-item">
              <i class="fab fa-react"></i>
              <span>React</span>
            </div>
            <div class="tech-item">
              <i class="fab fa-node-js"></i>
              <span>Node.js</span>
            </div>
            <div class="tech-item">
              <i class="fab fa-aws"></i>
              <span>AWS</span>
            </div>
            <div class="tech-item">
              <i class="fab fa-docker"></i>
              <span>Docker</span>
            </div>
            <div class="tech-item">
              <i class="fas fa-database"></i>
              <span>Database</span>
            </div>
          </div>
          <div class="center-logo">
            <div class="logo-circle">
              <i class="fas fa-laptop-code"></i>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="scroll-indicator" @click="scrollTo('about')">
      <div class="scroll-arrow"></div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  name: {
    type: String,
    default: 'John Doe'
  },
  title: {
    type: String,
    default: 'Expert IT Solutions & Digital Transformation'
  },
  description: {
    type: String,
    default: 'I help businesses leverage cutting-edge technology to increase efficiency, reduce costs, and accelerate growth. Specialized in modern web development, cloud solutions, and digital transformation strategies.'
  },
  profileImage: {
    type: String,
    default: 'https://via.placeholder.com/300x300/1B3C53/D2C1B6?text=IT+Expert'
  },
  socialLinks: {
    type: Array,
    default: () => [
      { name: 'GitHub', url: 'https://github.com', icon: 'fab fa-github' },
      { name: 'LinkedIn', url: 'https://linkedin.com', icon: 'fab fa-linkedin' },
      { name: 'Twitter', url: 'https://twitter.com', icon: 'fab fa-twitter' },
      { name: 'Instagram', url: 'https://instagram.com', icon: 'fab fa-instagram' }
    ]
  }
})

const scrollTo = (elementId) => {
  const element = document.getElementById(elementId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 5%;
  background: linear-gradient(135deg, #1B3C53 0%, #456882 100%);
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="20" height="20" patternUnits="userSpaceOnUse"><path d="M 20 0 L 0 0 0 20" fill="none" stroke="rgba(210,193,182,0.1)" stroke-width="1"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
  opacity: 0.5;
}

.hero-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  max-width: 1200px;
  width: 100%;
  align-items: center;
  position: relative;
  z-index: 1;
}

.hero-text {
  color: white;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(210, 193, 182, 0.2);
  padding: 8px 16px;
  border-radius: 25px;
  font-size: 0.9rem;
  margin-bottom: 1.5rem;
  border: 1px solid rgba(210, 193, 182, 0.3);
}

.hero-badge i {
  color: #D2C1B6;
}

.hero-title {
  font-size: 3.2rem;
  font-weight: 700;
  margin-bottom: 1rem;
  line-height: 1.1;
}

.highlight {
  color: #D2C1B6;
  background: linear-gradient(45deg, #D2C1B6, #456882);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-size: 1.3rem;
  font-weight: 500;
  margin-bottom: 1.5rem;
  opacity: 0.9;
  color: #D2C1B6;
}

.hero-description {
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 2rem;
  opacity: 0.8;
}

.value-props {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 2.5rem;
  flex-wrap: wrap;
}

.value-prop {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background: rgba(69, 104, 130, 0.3);
  padding: 8px 16px;
  border-radius: 20px;
  font-size: 0.9rem;
  border: 1px solid rgba(210, 193, 182, 0.2);
}

.value-prop i {
  color: #D2C1B6;
  font-size: 1rem;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
}

.btn {
  padding: 14px 28px;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.btn-primary {
  background: #D2C1B6;
  color: #1B3C53;
}

.btn-primary:hover {
  background: #c4b3a3;
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(210, 193, 182, 0.3);
}

.btn-secondary {
  background: transparent;
  color: #D2C1B6;
  border: 2px solid #D2C1B6;
}

.btn-secondary:hover {
  background: #D2C1B6;
  color: #1B3C53;
  transform: translateY(-2px);
}

.trust-indicators {
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
}

.trust-item {
  text-align: center;
}

.trust-item strong {
  display: block;
  font-size: 1.8rem;
  color: #D2C1B6;
  font-weight: 700;
  margin-bottom: 0.3rem;
}

.trust-item span {
  font-size: 0.9rem;
  opacity: 0.8;
}

.hero-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.tech-showcase {
  position: relative;
  width: 400px;
  height: 400px;
}

.tech-grid {
  position: absolute;
  width: 100%;
  height: 100%;
}

.tech-item {
  position: absolute;
  background: rgba(210, 193, 182, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(210, 193, 182, 0.2);
  border-radius: 15px;
  padding: 1rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
  animation: float 3s ease-in-out infinite;
}

.tech-item:nth-child(1) { top: 0; left: 50%; transform: translateX(-50%); animation-delay: 0s; }
.tech-item:nth-child(2) { top: 25%; right: 0; animation-delay: 0.5s; }
.tech-item:nth-child(3) { bottom: 25%; right: 0; animation-delay: 1s; }
.tech-item:nth-child(4) { bottom: 0; left: 50%; transform: translateX(-50%); animation-delay: 1.5s; }
.tech-item:nth-child(5) { bottom: 25%; left: 0; animation-delay: 2s; }
.tech-item:nth-child(6) { top: 25%; left: 0; animation-delay: 2.5s; }

.tech-item:hover {
  background: rgba(210, 193, 182, 0.2);
  transform: scale(1.1);
}

.tech-item i {
  font-size: 1.5rem;
  color: #D2C1B6;
}

.tech-item span {
  font-size: 0.8rem;
  color: white;
  font-weight: 500;
}

.center-logo {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.logo-circle {
  width: 100px;
  height: 100px;
  background: linear-gradient(135deg, #D2C1B6, #456882);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  animation: pulse 2s infinite;
}

.logo-circle i {
  font-size: 2.5rem;
  color: #1B3C53;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

@keyframes pulse {
  0% { transform: translate(-50%, -50%) scale(1); }
  50% { transform: translate(-50%, -50%) scale(1.05); }
  100% { transform: translate(-50%, -50%) scale(1); }
}

.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  cursor: pointer;
  animation: bounce 2s infinite;
}

.scroll-arrow {
  width: 20px;
  height: 20px;
  border-right: 2px solid #D2C1B6;
  border-bottom: 2px solid #D2C1B6;
  transform: rotate(45deg);
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
  40% { transform: translateX(-50%) translateY(-10px); }
  60% { transform: translateX(-50%) translateY(-5px); }
}

@media (max-width: 768px) {
  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
    gap: 2rem;
  }
  
  .hero-title {
    font-size: 2.2rem;
  }
  
  .hero-buttons {
    justify-content: center;
    flex-direction: column;
  }
  
  .value-props {
    justify-content: center;
  }
  
  .trust-indicators {
    justify-content: center;
  }
  
  .tech-showcase {
    width: 300px;
    height: 300px;
  }
  
  .tech-item {
    padding: 0.8rem;
  }
  
  .logo-circle {
    width: 80px;
    height: 80px;
  }
  
  .logo-circle i {
    font-size: 2rem;
  }
}
</style>