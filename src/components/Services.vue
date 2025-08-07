<template>
  <section id="services" class="services">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Enterprise IT Solutions</h2>
        <p class="section-subtitle">Strategic technology services designed to transform your business operations and drive measurable growth</p>
      </div>
      
      <div class="services-grid">
        <div v-for="(service, index) in services" :key="service.title" 
             class="service-card" 
             :class="{ featured: service.featured }"
             @mouseenter="handleHover(index, true)"
             @mouseleave="handleHover(index, false)">
          <div class="service-icon">
            <i :class="service.icon"></i>
          </div>
          <h3 class="service-title">{{ service.title }}</h3>
          <p class="service-description">{{ service.description }}</p>
          <ul class="service-features">
            <li v-for="feature in service.features" :key="feature">
              <i class="fas fa-check"></i>
              {{ feature }}
            </li>
          </ul>
          <div class="service-pricing">
            <span class="price">{{ service.price }}</span>
            <span class="price-note">{{ service.priceNote }}</span>
          </div>
          <button class="btn btn-service" @click="contactForService(service.title)">
            Get Quote
          </button>
        </div>
      </div>
      
      <div class="process-section">
        <h3>Enterprise Development Process</h3>
        <div class="process-steps">
          <div v-for="(step, index) in processSteps" :key="step.title" class="process-step">
            <div class="step-number">{{ index + 1 }}</div>
            <div class="step-content">
              <h4>{{ step.title }}</h4>
              <p>{{ step.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const hoveredCard = ref(-1)

const services = ref([
  {
    title: 'Enterprise Web Development',
    description: 'Scalable web applications designed for high-traffic enterprise environments with 99.9% uptime guarantee.',
    icon: 'fas fa-globe',
    features: [
      'Enterprise-grade Security',
      'Scalable Architecture',
      'Performance Optimization',
      'Real-time Analytics',
      'Multi-tenant Support'
    ],
    price: 'Starting at $15,000',
    priceNote: 'per project',
    featured: false
  },
  {
    title: 'Cloud Infrastructure & DevOps',
    description: 'Complete cloud migration and DevOps implementation to reduce costs by 40% while improving performance.',
    icon: 'fas fa-cloud',
    features: [
      'AWS/Azure/GCP Setup',
      'CI/CD Pipeline Implementation',
      'Auto-scaling & Load Balancing',
      'Monitoring & Alerting',
      'Cost Optimization'
    ],
    price: 'Starting at $25,000',
    priceNote: 'per project',
    featured: true
  },
  {
    title: 'Digital Transformation Consulting',
    description: 'Strategic IT consulting to modernize your business processes and technology infrastructure.',
    icon: 'fas fa-chart-line',
    features: [
      'Technology Assessment',
      'Digital Strategy Planning',
      'Process Optimization',
      'Team Training & Support',
      'ROI Measurement'
    ],
    price: '$300/hour',
    priceNote: 'consulting rate',
    featured: false
  },
  {
    title: 'API Integration & Development',
    description: 'Seamless third-party integrations and custom API development for enterprise applications.',
    icon: 'fas fa-code-branch',
    features: [
      'RESTful & GraphQL APIs',
      'Third-party Integrations',
      'Authentication & Security',
      'Real-time Data Processing',
      'API Documentation'
    ],
    price: 'Starting at $8,000',
    priceNote: 'per integration',
    featured: false
  },
  {
    title: 'Database Design & Optimization',
    description: 'Enterprise database solutions designed for high performance and data integrity.',
    icon: 'fas fa-database',
    features: [
      'Database Architecture',
      'Performance Optimization',
      'Data Security & Backup',
      'Migration Services',
      'Monitoring & Maintenance'
    ],
    price: 'Starting at $5,000',
    priceNote: 'per database',
    featured: false
  },
  {
    title: 'Enterprise Support & Maintenance',
    description: '24/7 enterprise-grade support with guaranteed SLA and proactive monitoring.',
    icon: 'fas fa-tools',
    features: [
      '24/7 Monitoring & Support',
      'Proactive Issue Resolution',
      'Performance Optimization',
      'Security Updates & Patches',
      'SLA Guarantee'
    ],
    price: 'Starting at $2,500',
    priceNote: 'per month',
    featured: false
  }
])

const processSteps = ref([
  {
    title: 'Business Analysis & Strategy',
    description: 'Comprehensive analysis of your business needs and technology requirements to create a strategic roadmap.'
  },
  {
    title: 'Architecture & Technical Design',
    description: 'Designing scalable, secure enterprise architecture with detailed technical specifications and documentation.'
  },
  {
    title: 'Agile Development & Implementation',
    description: 'Iterative development using industry best practices with regular client feedback and milestone deliveries.'
  },
  {
    title: 'Quality Assurance & Testing',
    description: 'Comprehensive testing including unit, integration, performance, and security testing for enterprise standards.'
  },
  {
    title: 'Deployment & Go-Live Support',
    description: 'Smooth production deployment with minimal downtime and dedicated go-live support team.'
  },
  {
    title: 'Ongoing Support & Optimization',
    description: 'Continuous monitoring, performance optimization, and proactive support to ensure business continuity.'
  }
])

const handleHover = (index, isHovering) => {
  hoveredCard.value = isHovering ? index : -1
}

const contactForService = (serviceTitle) => {
  // Scroll to contact section
  const contactSection = document.getElementById('contact')
  if (contactSection) {
    contactSection.scrollIntoView({ behavior: 'smooth' })
  }
  // You can also add logic to pre-fill contact form with selected service
  console.log(`Contact for service: ${serviceTitle}`)
}
</script>

<style scoped>
.services {
  padding: 100px 0;
  background: white;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 5%;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  color: #1B3C53;
  margin-bottom: 1rem;
}

.section-subtitle {
  font-size: 1.1rem;
  color: #456882;
  max-width: 600px;
  margin: 0 auto;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 5rem;
}

.service-card {
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  padding: 2.5rem;
  border-radius: 15px;
  text-align: center;
  transition: all 0.3s ease;
  border: 2px solid rgba(70, 104, 130, 0.1);
  position: relative;
  overflow: hidden;
  box-shadow: 0 8px 32px rgba(27, 60, 83, 0.1);
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(70, 104, 130, 0.1), transparent);
  transition: left 0.5s ease;
}

.service-card:hover::before {
  left: 100%;
}

.service-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(27, 60, 83, 0.2);
  border-color: #456882;
}

.service-card.featured {
  background: linear-gradient(135deg, #1B3C53 0%, #456882 100%);
  color: white;
  transform: scale(1.05);
}

.service-card.featured:hover {
  transform: scale(1.05) translateY(-10px);
}

.service-icon {
  width: 80px;
  height: 80px;
  background: #456882;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  font-size: 2rem;
  transition: all 0.3s ease;
}

.service-card.featured .service-icon {
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(10px);
}

.service-card:hover .service-icon {
  transform: rotateY(360deg);
}

.service-title {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: inherit;
}

.service-description {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
  opacity: 0.8;
}

.service-features {
  list-style: none;
  padding: 0;
  margin: 0 0 2rem 0;
  text-align: left;
}

.service-features li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 0.8rem;
  font-size: 0.9rem;
}

.service-features i {
  color: #456882;
  font-size: 0.8rem;
}

.service-card.featured .service-features i {
  color: #D2C1B6;
}

.service-pricing {
  margin-bottom: 2rem;
  padding: 1rem;
  background: rgba(70, 104, 130, 0.1);
  border-radius: 10px;
}

.service-card.featured .service-pricing {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
}

.price {
  display: block;
  font-size: 1.5rem;
  font-weight: 700;
  color: #1B3C53;
  margin-bottom: 0.3rem;
}

.service-card.featured .price {
  color: #D2C1B6;
}

.price-note {
  font-size: 0.9rem;
  opacity: 0.7;
}

.btn-service {
  background: #456882;
  color: white;
  border: none;
  padding: 12px 30px;
  border-radius: 25px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  width: 100%;
}

.btn-service:hover {
  background: #1B3C53;
  transform: translateY(-2px);
}

.service-card.featured .btn-service {
  background: #D2C1B6;
  color: #1B3C53;
}

.service-card.featured .btn-service:hover {
  background: rgba(210, 193, 182, 0.8);
}

.process-section {
  margin-top: 5rem;
  text-align: center;
}

.process-section h3 {
  font-size: 2rem;
  color: #1B3C53;
  margin-bottom: 3rem;
}

.process-steps {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.process-step {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  text-align: left;
  padding: 1.5rem;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(70, 104, 130, 0.1);
  transition: all 0.3s ease;
  box-shadow: 0 4px 16px rgba(27, 60, 83, 0.1);
}

.process-step:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(27, 60, 83, 0.2);
}

.step-number {
  width: 40px;
  height: 40px;
  background: #456882;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  flex-shrink: 0;
}

.step-content h4 {
  font-size: 1.2rem;
  color: #1B3C53;
  margin-bottom: 0.5rem;
}

.step-content p {
  color: #456882;
  line-height: 1.6;
  font-size: 0.95rem;
}

@media (max-width: 768px) {
  .services-grid {
    grid-template-columns: 1fr;
  }
  
  .service-card.featured {
    transform: none;
  }
  
  .service-card.featured:hover {
    transform: translateY(-10px);
  }
  
  .process-steps {
    grid-template-columns: 1fr;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>
