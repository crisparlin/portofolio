<template>
  <section id="portfolio" class="portfolio">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">Enterprise Project Portfolio</h2>
        <p class="section-subtitle">Delivering scalable solutions for businesses across industries with proven ROI</p>
      </div>
      
      <div class="filter-tabs">
        <button 
          v-for="category in categories" 
          :key="category"
          :class="{ active: activeFilter === category }"
          @click="filterProjects(category)"
          class="filter-btn">
          {{ category }}
        </button>
      </div>
      
      <div class="portfolio-grid">
        <div 
          v-for="project in filteredProjects" 
          :key="project.id"
          class="portfolio-item"
          @click="openModal(project)">
          <div class="portfolio-image">
            <img :src="project.image" :alt="project.title">
            <div class="portfolio-overlay">
              <div class="overlay-content">
                <h3>{{ project.title }}</h3>
                <p>{{ project.shortDescription }}</p>
                <div class="project-tags">
                  <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
                </div>
                <div class="project-links">
                  <a v-if="project.liveUrl" :href="project.liveUrl" target="_blank" class="project-link" @click.stop>
                    <i class="fas fa-external-link-alt"></i> Live Demo
                  </a>
                  <a v-if="project.githubUrl" :href="project.githubUrl" target="_blank" class="project-link" @click.stop>
                    <i class="fab fa-github"></i> Code
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Modal -->
      <div v-if="selectedProject" class="modal-overlay" @click="closeModal">
        <div class="modal-content" @click.stop>
          <button class="modal-close" @click="closeModal">
            <i class="fas fa-times"></i>
          </button>
          <div class="modal-header">
            <img :src="selectedProject.image" :alt="selectedProject.title" class="modal-image">
            <div class="modal-info">
              <h3>{{ selectedProject.title }}</h3>
              <p class="modal-description">{{ selectedProject.fullDescription }}</p>
              <div class="modal-tags">
                <span v-for="tag in selectedProject.tags" :key="tag" class="tag">{{ tag }}</span>
              </div>
            </div>
          </div>
          <div class="modal-details">
            <div class="project-features">
              <h4>Key Features:</h4>
              <ul>
                <li v-for="feature in selectedProject.features" :key="feature">{{ feature }}</li>
              </ul>
            </div>
            <div class="project-tech">
              <h4>Technologies Used:</h4>
              <div class="tech-stack">
                <span v-for="tech in selectedProject.technologies" :key="tech" class="tech-item">{{ tech }}</span>
              </div>
            </div>
          </div>
          <div class="modal-actions">
            <a v-if="selectedProject.liveUrl" :href="selectedProject.liveUrl" target="_blank" class="btn btn-primary">
              <i class="fas fa-external-link-alt"></i> Live Demo
            </a>
            <a v-if="selectedProject.githubUrl" :href="selectedProject.githubUrl" target="_blank" class="btn btn-secondary">
              <i class="fab fa-github"></i> View Code
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed, ref } from 'vue'

const activeFilter = ref('All')
const selectedProject = ref(null)

const categories = ['All', 'Enterprise Web Apps', 'Cloud Solutions', 'API Development', 'Database Systems', 'Digital Transformation']

const projects = ref([
  {
    id: 1,
    title: 'Enterprise Resource Planning System',
    shortDescription: 'Comprehensive ERP solution increasing operational efficiency by 45%',
    fullDescription: 'A scalable Enterprise Resource Planning system built for a Fortune 500 manufacturing company, integrating inventory management, financial reporting, human resources, and supply chain operations. Reduced operational costs by 30% and improved data accuracy by 95%.',
    category: 'Enterprise Web Apps',
    image: 'https://via.placeholder.com/600x400/1B3C53/ffffff?text=ERP+System',
    tags: ['Vue.js', 'Node.js', 'PostgreSQL', 'AWS'],
    technologies: ['Vue 3', 'Express.js', 'PostgreSQL', 'AWS EC2', 'Redis', 'Docker', 'Kubernetes'],
    features: [
      'Multi-module integration (Finance, HR, Inventory)',
      'Real-time dashboard with KPIs',
      'Role-based access control',
      'Automated reporting and analytics',
      'API integrations with third-party systems',
      'Cloud-native architecture',
      '99.9% uptime guarantee'
    ],
    clientResults: '45% increase in operational efficiency, 30% cost reduction',
    liveUrl: null,
    githubUrl: null
  },
  {
    id: 2,
    title: 'Multi-Cloud Infrastructure Migration',
    shortDescription: 'Complete cloud migration reducing infrastructure costs by 40%',
    fullDescription: 'Led the migration of legacy on-premise infrastructure to a multi-cloud environment using AWS and Azure. Implemented DevOps practices, automated deployment pipelines, and established monitoring systems for a financial services company.',
    category: 'Cloud Solutions',
    image: 'https://via.placeholder.com/600x400/456882/ffffff?text=Cloud+Migration',
    tags: ['AWS', 'Azure', 'Docker', 'Kubernetes'],
    technologies: ['AWS Services', 'Azure Cloud', 'Docker', 'Kubernetes', 'Terraform', 'Jenkins', 'Prometheus'],
    features: [
      'Multi-cloud architecture design',
      'Automated CI/CD pipelines',
      'Infrastructure as Code (IaC)',
      'Monitoring and alerting systems',
      'Auto-scaling and load balancing',
      'Disaster recovery implementation',
      'Security compliance (SOC 2, PCI DSS)'
    ],
    clientResults: '40% cost reduction, 60% faster deployments, zero downtime',
    liveUrl: null,
    githubUrl: null
  },
  {
    id: 3,
    title: 'Real-time Analytics Platform',
    shortDescription: 'Big data analytics platform processing 10M+ events daily',
    fullDescription: 'Developed a high-performance real-time analytics platform capable of processing over 10 million events daily. Built for an e-commerce giant to provide instant insights into customer behavior, sales trends, and inventory optimization.',
    category: 'Enterprise Web Apps',
    image: 'https://via.placeholder.com/600x400/D2C1B6/1B3C53?text=Analytics+Platform',
    tags: ['Apache Kafka', 'Elasticsearch', 'Node.js', 'React'],
    technologies: ['Apache Kafka', 'Elasticsearch', 'Node.js', 'React', 'Redis', 'MongoDB', 'AWS Kinesis'],
    features: [
      'Real-time stream processing with Kafka',
      'Advanced search with Elasticsearch',
      'Interactive data visualizations',
      'Custom alert and notification system',
      'Machine learning integration',
      'Horizontal scaling architecture',
      'Sub-second query response time'
    ],
    clientResults: '300% improvement in data processing speed, $2M+ in cost savings',
    liveUrl: null,
    githubUrl: null
  },
  {
    id: 4,
    title: 'Enterprise API Gateway',
    shortDescription: 'Centralized API management for 50+ microservices',
    fullDescription: 'Designed and implemented a comprehensive API gateway solution managing over 50 microservices for a tech unicorn. Includes rate limiting, authentication, monitoring, and automated documentation generation.',
    category: 'API Development',
    image: 'https://via.placeholder.com/600x400/456882/ffffff?text=API+Gateway',
    tags: ['Kong', 'Node.js', 'Docker', 'Kubernetes'],
    technologies: ['Kong Gateway', 'Node.js', 'Docker', 'Kubernetes', 'PostgreSQL', 'Prometheus', 'Grafana'],
    features: [
      'Centralized API management',
      'OAuth 2.0 and JWT authentication',
      'Rate limiting and throttling',
      'API versioning and deprecation',
      'Real-time monitoring and analytics',
      'Automated documentation generation',
      'Load balancing and health checks'
    ],
    clientResults: '99.99% API uptime, 50% reduction in response time',
    liveUrl: null,
    githubUrl: null
  },
  {
    id: 5,
    title: 'High-Performance Database Optimization',
    shortDescription: 'Database optimization reducing query time by 85%',
    fullDescription: 'Complete database architecture overhaul for a fintech company processing millions of transactions daily. Implemented advanced indexing, query optimization, and database sharding strategies.',
    category: 'Database Systems',
    image: 'https://via.placeholder.com/600x400/1B3C53/D2C1B6?text=Database+Optimization',
    tags: ['PostgreSQL', 'Redis', 'MongoDB'],
    technologies: ['PostgreSQL', 'Redis', 'MongoDB', 'Apache Kafka', 'Elasticsearch', 'Docker'],
    features: [
      'Advanced query optimization',
      'Database sharding and partitioning',
      'Caching layer implementation',
      'Real-time data replication',
      'Automated backup and recovery',
      'Performance monitoring and tuning',
      'ACID compliance maintenance'
    ],
    clientResults: '85% faster query performance, 99.99% data availability',
    liveUrl: null,
    githubUrl: null
  },
  {
    id: 6,
    title: 'Digital Transformation Initiative',
    shortDescription: 'Complete digital overhaul for traditional retail chain',
    fullDescription: 'Led a comprehensive digital transformation project for a 200-store retail chain, implementing omnichannel solutions, inventory management, and customer analytics platform.',
    category: 'Digital Transformation',
    image: 'https://via.placeholder.com/600x400/D2C1B6/1B3C53?text=Digital+Transformation',
    tags: ['Vue.js', 'Python', 'AWS', 'Salesforce'],
    technologies: ['Vue.js', 'Python', 'AWS Services', 'Salesforce', 'Shopify Plus', 'Tableau'],
    features: [
      'Omnichannel customer experience',
      'Real-time inventory synchronization',
      'Customer analytics and insights',
      'Staff training and adoption programs',
      'Legacy system integration',
      'Performance monitoring dashboards',
      'Mobile POS implementation',
      'Multi-location management'
    ],
    clientResults: '200% increase in online sales, 35% improvement in customer satisfaction',
    liveUrl: null,
    githubUrl: null
  }
])

const filteredProjects = computed(() => {
  if (activeFilter.value === 'All') {
    return projects.value
  }
  return projects.value.filter(project => project.category === activeFilter.value)
})

const filterProjects = (category) => {
  activeFilter.value = category
}

const openModal = (project) => {
  selectedProject.value = project
  document.body.style.overflow = 'hidden'
}

const closeModal = () => {
  selectedProject.value = null
  document.body.style.overflow = 'auto'
}
</script>

<style scoped>
.portfolio {
  padding: 100px 0;
  background: #f8f9fa;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 5%;
}

.section-header {
  text-align: center;
  margin-bottom: 3rem;
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

.filter-tabs {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 3rem;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 10px 25px;
  border: 2px solid #456882;
  background: transparent;
  color: #456882;
  border-radius: 25px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 500;
}

.filter-btn:hover,
.filter-btn.active {
  background: #456882;
  color: white;
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.portfolio-item {
  cursor: pointer;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 5px 15px rgba(27, 60, 83, 0.1);
  transition: all 0.3s ease;
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(70, 104, 130, 0.1);
}

.portfolio-item:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 40px rgba(27, 60, 83, 0.2);
}

.portfolio-image {
  position: relative;
  overflow: hidden;
  height: 250px;
}

.portfolio-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}

.portfolio-item:hover .portfolio-image img {
  transform: scale(1.1);
}

.portfolio-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(27, 60, 83, 0.95);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.portfolio-item:hover .portfolio-overlay {
  opacity: 1;
}

.overlay-content {
  text-align: center;
  color: white;
  padding: 2rem;
}

.overlay-content h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.overlay-content p {
  margin-bottom: 1.5rem;
  opacity: 0.9;
}

.project-tags {
  display: flex;
  justify-content: center;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
  flex-wrap: wrap;
}

.tag {
  background: #456882;
  color: white;
  padding: 4px 12px;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 500;
}

.project-links {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.project-link {
  color: white;
  text-decoration: none;
  padding: 8px 16px;
  border: 1px solid white;
  border-radius: 20px;
  transition: all 0.3s ease;
  font-size: 0.9rem;
}

.project-link:hover {
  background: #D2C1B6;
  color: #1B3C53;
  border-color: #D2C1B6;
}

/* Modal Styles */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 2rem;
}

.modal-content {
  background: white;
  border-radius: 15px;
  max-width: 800px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
}

.modal-close {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #456882;
  z-index: 1001;
  padding: 5px;
}

.modal-header {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  padding: 2rem;
  align-items: start;
}

.modal-image {
  width: 100%;
  border-radius: 10px;
}

.modal-info h3 {
  font-size: 1.8rem;
  color: #1B3C53;
  margin-bottom: 1rem;
}

.modal-description {
  color: #456882;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.modal-tags {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

.modal-details {
  padding: 0 2rem 2rem;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
}

.project-features h4,
.project-tech h4 {
  color: #1B3C53;
  margin-bottom: 1rem;
}

.project-features ul {
  list-style: none;
  padding: 0;
}

.project-features li {
  padding: 0.5rem 0;
  border-bottom: 1px solid rgba(70, 104, 130, 0.1);
  color: #456882;
}

.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tech-item {
  background: rgba(210, 193, 182, 0.2);
  color: #1B3C53;
  padding: 6px 12px;
  border-radius: 20px;
  font-size: 0.9rem;
  border: 1px solid rgba(70, 104, 130, 0.2);
}

.modal-actions {
  padding: 0 2rem 2rem;
  display: flex;
  gap: 1rem;
  justify-content: center;
}

.btn {
  padding: 12px 30px;
  border: none;
  border-radius: 25px;
  text-decoration: none;
  font-weight: 600;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

.btn-primary {
  background: #456882;
  color: white;
}

.btn-primary:hover {
  background: #1B3C53;
}

.btn-secondary {
  background: transparent;
  color: #456882;
  border: 2px solid #456882;
}

.btn-secondary:hover {
  background: #456882;
  color: white;
}

@media (max-width: 768px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }
  
  .modal-header {
    grid-template-columns: 1fr;
  }
  
  .modal-details {
    grid-template-columns: 1fr;
  }
  
  .filter-tabs {
    justify-content: center;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .modal-actions {
    flex-direction: column;
  }
}
</style>
