<template>
  <section id="portfolio" class="portfolio">
    <div class="container">
      <h2 class="section-title">Featured Projects</h2>
      <div class="portfolio-filters">
        <button 
          v-for="filter in portfolioFilters" 
          :key="filter"
          @click="activeFilter = filter"
          :class="{ 'active': activeFilter === filter }"
          class="filter-btn"
        >
          {{ filter }}
        </button>
      </div>
      <div class="portfolio-grid">
        <div 
          v-for="project in filteredProjects" 
          :key="project.id"
          class="portfolio-item"
          @click="openModal(project)"
        >
          <div class="portfolio-image">
            <div class="image-placeholder">
              <i :class="project.icon"></i>
            </div>
            <div class="portfolio-overlay">
              <h3>{{ project.title }}</h3>
              <p>{{ project.category }}</p>
              <button class="view-btn">View Details</button>
            </div>
          </div>
          <div class="portfolio-info">
            <h3>{{ project.title }}</h3>
            <p>{{ project.shortDesc }}</p>
            <div class="project-tags">
              <span v-for="tech in project.technologies" :key="tech" class="tag">{{ tech }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Project Modal -->
    <div v-if="selectedProject" class="modal" @click="closeModal">
      <div class="modal-content" @click.stop>
        <button class="modal-close" @click="closeModal">
          <i class="fas fa-times"></i>
        </button>
        <h2>{{ selectedProject.title }}</h2>
        <p class="modal-category">{{ selectedProject.category }}</p>
        <div class="modal-body">
          <p>{{ selectedProject.fullDesc }}</p>
          <h3>Key Features:</h3>
          <ul>
            <li v-for="feature in selectedProject.features" :key="feature">{{ feature }}</li>
          </ul>
          <h3>Technologies Used:</h3>
          <div class="project-tags">
            <span v-for="tech in selectedProject.technologies" :key="tech" class="tag">{{ tech }}</span>
          </div>
          <h3>Impact:</h3>
          <p>{{ selectedProject.impact }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeFilter = ref('All')
const selectedProject = ref(null)

const portfolioFilters = ['All', 'Web Apps', 'ERP Systems', 'APIs', 'Cloud Solutions']

const projects = ref([
  {
    id: 1,
    title: 'ERP System for Pawnshop',
    category: 'ERP Systems',
    shortDesc: 'Comprehensive ERP system for managing pawnshop operations',
    fullDesc: 'Developed a full-featured ERP system for a pawnshop company, handling all aspects of business operations from order submission to financial reporting.',
    icon: 'fas fa-store',
    technologies: ['Vue.js', 'Node.js', 'PostgreSQL', 'Express', 'Redis'],
    features: [
      'Order submission and tracking system',
      'Real-time inventory monitoring for goods',
      'Financial management module for redemption and sales',
      'Automated journal entry system for accounting',
      'Integration with existing financial systems',
      'Role-based access control',
      'Comprehensive reporting dashboard'
    ],
    impact: 'Improved operational efficiency by 60%, reduced manual errors by 80%, and streamlined financial reporting process.'
  },
  {
    id: 2,
    title: 'E-Commerce Platform',
    category: 'Web Apps',
    shortDesc: 'Scalable e-commerce solution with microservices architecture',
    fullDesc: 'Led the development of a high-performance e-commerce platform serving 100K+ daily users.',
    icon: 'fas fa-shopping-cart',
    technologies: ['React', 'Node.js', 'MongoDB', 'AWS', 'Docker'],
    features: [
      'Product catalog management',
      'Shopping cart and checkout',
      'Payment gateway integration',
      'Order tracking system',
      'Admin dashboard',
      'Customer reviews and ratings'
    ],
    impact: 'Handled 10K+ concurrent users with 99.9% uptime, increased conversion rate by 35%.'
  },
  {
    id: 3,
    title: 'Real-time Analytics Dashboard',
    category: 'Web Apps',
    shortDesc: 'Business intelligence dashboard with real-time data visualization',
    fullDesc: 'Built a comprehensive analytics platform for monitoring business metrics and KPIs in real-time.',
    icon: 'fas fa-chart-line',
    technologies: ['Vue.js', 'D3.js', 'Node.js', 'ElasticSearch', 'WebSocket'],
    features: [
      'Real-time data visualization',
      'Custom report builder',
      'Export functionality',
      'Alert system for KPI thresholds',
      'Multi-tenant architecture',
      'Historical data analysis'
    ],
    impact: 'Reduced reporting time from hours to seconds, improved decision-making speed by 50%.'
  },
  {
    id: 4,
    title: 'RESTful API Gateway',
    category: 'APIs',
    shortDesc: 'Microservices API gateway with authentication and rate limiting',
    fullDesc: 'Designed and implemented a robust API gateway for managing multiple microservices.',
    icon: 'fas fa-network-wired',
    technologies: ['Node.js', 'Express', 'Redis', 'JWT', 'Docker'],
    features: [
      'API authentication and authorization',
      'Rate limiting and throttling',
      'Request/response transformation',
      'API versioning',
      'Logging and monitoring',
      'Caching layer'
    ],
    impact: 'Handled 1M+ API requests daily, reduced response time by 40%.'
  },
  {
    id: 5,
    title: 'Cloud Migration Project',
    category: 'Cloud Solutions',
    shortDesc: 'Migrated legacy applications to AWS cloud infrastructure',
    fullDesc: 'Led the migration of monolithic applications to cloud-native microservices on AWS.',
    icon: 'fas fa-cloud-upload-alt',
    technologies: ['AWS', 'Docker', 'Kubernetes', 'Terraform', 'Jenkins'],
    features: [
      'Infrastructure as Code',
      'Auto-scaling configuration',
      'Load balancing setup',
      'CI/CD pipeline',
      'Monitoring and alerting',
      'Disaster recovery plan'
    ],
    impact: 'Reduced infrastructure costs by 40%, improved deployment frequency by 10x.'
  },
  {
    id: 6,
    title: 'Customer Management System',
    category: 'Web Apps',
    shortDesc: 'CRM system for managing customer relationships and sales pipeline',
    fullDesc: 'Developed a feature-rich CRM system to streamline sales and customer service processes.',
    icon: 'fas fa-users',
    technologies: ['Vue.js', 'Laravel', 'MySQL', 'Redis', 'AWS'],
    features: [
      'Contact management',
      'Sales pipeline tracking',
      'Email integration',
      'Task and calendar management',
      'Reporting and analytics',
      'Mobile responsive design'
    ],
    impact: 'Increased sales team productivity by 45%, improved customer satisfaction score by 30%.'
  }
])

const filteredProjects = computed(() => {
  if (activeFilter.value === 'All') {
    return projects.value
  }
  return projects.value.filter(project => project.category === activeFilter.value)
})

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
  padding: 80px 0;
  background: #F9FAFB;
  transition: background-color 0.3s ease;
}

@media (prefers-color-scheme: dark) {
  .portfolio {
    background: #0F172A;
  }
}

.portfolio-filters {
  display: flex;
  justify-content: center;
  gap: 15px;
  margin-bottom: 40px;
  flex-wrap: wrap;
}

.filter-btn {
  padding: 12px 30px;
  background: #FFFFFF;
  border: 2px solid #1E3A8A;
  border-radius: 25px;
  color: #1E3A8A;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(30, 58, 138, 0.1);
}

.filter-btn:hover,
.filter-btn.active {
  background: #1E3A8A;
  color: white;
  border-color: #1E3A8A;
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(30, 58, 138, 0.3);
}

@media (prefers-color-scheme: dark) {
  .filter-btn {
    background: #1E293B;
    border-color: #2563EB;
    color: #2563EB;
    box-shadow: 0 4px 15px rgba(37, 99, 235, 0.2);
  }
  
  .filter-btn:hover,
  .filter-btn.active {
    background: #2563EB;
    color: white;
    border-color: #2563EB;
    box-shadow: 0 8px 25px rgba(37, 99, 235, 0.4);
  }
}

.portfolio-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.portfolio-item {
  cursor: pointer;
  border-radius: 16px;
  overflow: hidden;
  background: #FFFFFF;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  transition: all 0.4s ease;
  border: 2px solid transparent;
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
  position: relative;
}

.portfolio-item::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
  transition: left 0.5s ease;
  z-index: 1;
  pointer-events: none;
}

.portfolio-item:hover::before {
  left: 100%;
}

.portfolio-item:nth-child(1) { animation-delay: 0.1s; }
.portfolio-item:nth-child(2) { animation-delay: 0.2s; }
.portfolio-item:nth-child(3) { animation-delay: 0.3s; }
.portfolio-item:nth-child(4) { animation-delay: 0.4s; }
.portfolio-item:nth-child(5) { animation-delay: 0.5s; }
.portfolio-item:nth-child(6) { animation-delay: 0.6s; }

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

.portfolio-item:hover {
  transform: translateY(-12px) scale(1.02);
  box-shadow: 0 20px 40px rgba(30, 58, 138, 0.25);
  border-color: #14B8A6;
}

@media (prefers-color-scheme: dark) {
  .portfolio-item {
    background: #1E293B;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
  }
  
  .portfolio-item:hover {
    box-shadow: 0 20px 40px rgba(37, 99, 235, 0.3);
    border-color: #10B981;
  }
}

.portfolio-image {
  position: relative;
  overflow: hidden;
  height: 280px;
  background: linear-gradient(135deg, #1E3A8A 0%, #14B8A6 100%);
}

.portfolio-item:nth-child(1) .portfolio-image {
  background: linear-gradient(135deg, #F59E0B 0%, #D97706 100%);
}

.portfolio-item:nth-child(2) .portfolio-image {
  background: linear-gradient(135deg, #1E3A8A 0%, #2563EB 100%);
}

.portfolio-item:nth-child(3) .portfolio-image {
  background: linear-gradient(135deg, #14B8A6 0%, #10B981 100%);
}

.portfolio-item:nth-child(4) .portfolio-image {
  background: linear-gradient(135deg, #2563EB 0%, #1E3A8A 100%);
}

.portfolio-item:nth-child(5) .portfolio-image {
  background: linear-gradient(135deg, #10B981 0%, #14B8A6 100%);
}

.portfolio-item:nth-child(6) .portfolio-image {
  background: linear-gradient(135deg, #1E3A8A 0%, #14B8A6 50%, #F59E0B 100%);
}

.portfolio-image .image-placeholder {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 90px;
  color: rgba(255, 255, 255, 0.4);
  border: none;
  border-radius: 0;
  transition: all 0.3s ease;
}

.portfolio-item:hover .image-placeholder {
  transform: scale(1.1);
  color: rgba(255, 255, 255, 0.6);
}

.portfolio-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(30, 58, 138, 0.97) 0%, rgba(20, 184, 166, 0.97) 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.4s ease;
  color: white;
  padding: 20px;
}

@media (prefers-color-scheme: dark) {
  .portfolio-overlay {
    background: linear-gradient(135deg, rgba(37, 99, 235, 0.97) 0%, rgba(16, 185, 129, 0.97) 100%);
  }
}

.portfolio-item:hover .portfolio-overlay {
  opacity: 1;
}

.portfolio-overlay h3 {
  margin-bottom: 10px;
  font-size: 1.5rem;
  font-weight: 800;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

.portfolio-overlay p {
  margin-bottom: 20px;
  font-size: 1rem;
  font-weight: 600;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
}

.view-btn {
  padding: 12px 30px;
  background: #F59E0B;
  color: white;
  border: none;
  border-radius: 8px;
  font-weight: 700;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(245, 158, 11, 0.3);
}

.view-btn:hover {
  transform: scale(1.1);
  background: #D97706;
  box-shadow: 0 8px 25px rgba(245, 158, 11, 0.5);
}

.portfolio-info {
  padding: 24px;
  background: #FFFFFF;
}

@media (prefers-color-scheme: dark) {
  .portfolio-info {
    background: #1E293B;
  }
}

.portfolio-info h3 {
  margin-bottom: 12px;
  color: var(--text-color);
  font-size: 1.3rem;
  font-weight: 700;
}

.portfolio-info p {
  color: var(--text-secondary);
  margin-bottom: 16px;
  font-size: 0.95rem;
  line-height: 1.6;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}

.tag {
  background: linear-gradient(135deg, #1E3A8A 0%, #2563EB 100%);
  color: white;
  padding: 6px 16px;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 700;
  box-shadow: 0 3px 10px rgba(30, 58, 138, 0.3);
  transition: all 0.3s ease;
  border: 1px solid rgba(255, 255, 255, 0.2);
}

/* Modal */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2000;
  padding: 20px;
}

.modal-content {
  background: var(--surface-color);
  border-radius: 15px;
  max-width: 800px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  padding: 40px;
  position: relative;
  transition: background-color 0.3s ease;
}

.modal-close {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: var(--background-color);
  border: none;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  color: var(--text-color);
  transition: all 0.3s ease;
}

.modal-close:hover {
  background: var(--primary-color);
  color: white;
}

.modal-content h2 {
  color: var(--text-color);
  margin-bottom: 10px;
  font-size: 2rem;
}

.modal-category {
  color: var(--primary-color);
  font-weight: 600;
  margin-bottom: 25px;
}

.modal-body h3 {
  color: var(--text-color);
  margin: 25px 0 15px;
  font-size: 1.3rem;
}

.modal-body p {
  color: var(--text-color);
  line-height: 1.8;
  margin-bottom: 15px;
}

.modal-body ul {
  margin-left: 20px;
  margin-bottom: 20px;
}

.modal-body li {
  color: var(--text-color);
  margin-bottom: 10px;
  line-height: 1.6;
}

/* Responsive Design */
@media (max-width: 968px) {
  .portfolio-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .portfolio-grid {
    grid-template-columns: 1fr;
  }

  .modal-content {
    padding: 30px 20px;
  }
}
</style>
