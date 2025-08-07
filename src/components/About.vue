<template>
  <section id="about" class="about">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">About Me</h2>
        <p class="section-subtitle">Get to know more about my background and expertise</p>
      </div>
      
      <div class="about-content">
        <div class="about-text">
          <h3>{{ aboutTitle }}</h3>
          <p class="about-description">{{ aboutDescription }}</p>
          
          <div class="skills-section">
            <h4>Technical Skills</h4>
            <div class="skills-grid">
              <div v-for="skill in skills" :key="skill.name" class="skill-item">
                <div class="skill-header">
                  <span class="skill-name">{{ skill.name }}</span>
                  <span class="skill-percentage">{{ skill.level }}%</span>
                </div>
                <div class="skill-bar">
                  <div class="skill-progress" :style="{ width: skill.level + '%' }"></div>
                </div>
              </div>
            </div>
          </div>
          
          <div class="experience-section">
            <h4>Experience Highlights</h4>
            <div class="experience-grid">
              <div v-for="exp in experience" :key="exp.title" class="experience-item">
                <div class="exp-icon">
                  <i :class="exp.icon"></i>
                </div>
                <div class="exp-content">
                  <h5>{{ exp.title }}</h5>
                  <p>{{ exp.description }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="about-stats">
          <div class="stats-grid">
            <div v-for="stat in stats" :key="stat.label" class="stat-item">
              <div class="stat-number">{{ stat.number }}</div>
              <div class="stat-label">{{ stat.label }}</div>
            </div>
          </div>
          
          <div class="certifications">
            <h4>Certifications & Education</h4>
            <div class="cert-list">
              <div v-for="cert in certifications" :key="cert.name" class="cert-item">
                <i class="fas fa-certificate"></i>
                <span>{{ cert.name }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
defineProps({
  aboutTitle: {
    type: String,
    default: 'Why Choose My IT Solutions?'
  },
  aboutDescription: {
    type: String,
    default: 'With 5+ years of proven experience delivering enterprise-grade solutions, I transform complex business challenges into streamlined digital processes. My approach combines cutting-edge technology with practical business insights to maximize your ROI and accelerate growth.'
  },
  skills: {
    type: Array,
    default: () => [
      { name: 'JavaScript/TypeScript', level: 95 },
      { name: 'Vue.js/React', level: 90 },
      { name: 'Node.js/Express', level: 85 },
      { name: 'Python/Django', level: 80 },
      { name: 'Cloud Platforms (AWS/Azure)', level: 75 },
      { name: 'Database Design (SQL/NoSQL)', level: 85 }
    ]
  },
  experience: {
    type: Array,
    default: () => [
      {
        title: 'Enterprise Web Development',
        description: 'Scalable web applications that handle millions of users and transactions with 99.9% uptime.',
        icon: 'fas fa-globe'
      },
      {
        title: 'Cloud Infrastructure & DevOps',
        description: 'Reduce infrastructure costs by 40% while improving performance and reliability.',
        icon: 'fas fa-cloud-upload-alt'
      },
      {
        title: 'Digital Transformation Consulting',
        description: 'Strategic technology roadmaps that position your business for future growth and competitiveness.',
        icon: 'fas fa-chart-line'
      },
      {
        title: 'Custom Software Solutions',
        description: 'Bespoke applications tailored to your unique business processes and requirements.',
        icon: 'fas fa-cogs'
      }
    ]
  },
  stats: {
    type: Array,
    default: () => [
      { number: '100+', label: 'Projects Delivered' },
      { number: '50+', label: 'Enterprise Clients' },
      { number: '99.9%', label: 'System Uptime' },
      { number: '40%', label: 'Cost Reduction' }
    ]
  },
  certifications: {
    type: Array,
    default: () => [
      { name: 'AWS Certified Solutions Architect' },
      { name: 'Google Cloud Professional Developer' },
      { name: 'Microsoft Azure Fundamentals' },
      { name: 'Certified Scrum Master (CSM)' }
    ]
  }
})
</script>

<style scoped>
.about {
  padding: 100px 0;
  background: #D2C1B6;
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

.about-content {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 4rem;
  align-items: start;
}

.about-text h3 {
  font-size: 1.8rem;
  color: #1B3C53;
  margin-bottom: 1.5rem;
}

.about-description {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #456882;
  margin-bottom: 2.5rem;
}

.skills-section {
  margin-bottom: 3rem;
}

.skills-section h4 {
  font-size: 1.3rem;
  color: #1B3C53;
  margin-bottom: 1.5rem;
}

.skills-grid {
  display: grid;
  gap: 1.5rem;
}

.skill-item {
  background: white;
  padding: 1.5rem;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(27, 60, 83, 0.1);
  border: 1px solid rgba(69, 104, 130, 0.1);
}

.skill-header {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
}

.skill-name {
  font-weight: 600;
  color: #1B3C53;
}

.skill-percentage {
  color: #456882;
  font-weight: 600;
}

.skill-bar {
  height: 8px;
  background: rgba(69, 104, 130, 0.2);
  border-radius: 4px;
  overflow: hidden;
}

.skill-progress {
  height: 100%;
  background: linear-gradient(90deg, #456882, #1B3C53);
  border-radius: 4px;
  transition: width 2s ease;
}

.experience-section h4 {
  font-size: 1.3rem;
  color: #1B3C53;
  margin-bottom: 1.5rem;
}

.experience-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.experience-item {
  display: flex;
  gap: 1rem;
  align-items: flex-start;
}

.exp-icon {
  width: 50px;
  height: 50px;
  background: #456882;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  flex-shrink: 0;
}

.exp-content h5 {
  color: #1B3C53;
  margin-bottom: 0.5rem;
  font-size: 1.1rem;
}

.exp-content p {
  color: #456882;
  font-size: 0.9rem;
  line-height: 1.5;
}

.about-stats {
  background: white;
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(27, 60, 83, 0.15);
  height: fit-content;
  position: sticky;
  top: 2rem;
  border: 1px solid rgba(69, 104, 130, 0.1);
}

.stats-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
  margin-bottom: 2.5rem;
}

.stat-item {
  text-align: center;
  padding: 1rem;
  border-radius: 10px;
  background: rgba(210, 193, 182, 0.3);
}

.stat-number {
  font-size: 2rem;
  font-weight: 700;
  color: #1B3C53;
  margin-bottom: 0.5rem;
}

.stat-label {
  font-size: 0.9rem;
  color: #456882;
}

.certifications h4 {
  font-size: 1.2rem;
  color: #1B3C53;
  margin-bottom: 1rem;
}

.cert-list {
  display: grid;
  gap: 0.8rem;
}

.cert-item {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  padding: 0.8rem;
  background: rgba(210, 193, 182, 0.3);
  border-radius: 8px;
  font-size: 0.9rem;
  color: #456882;
}

.cert-item i {
  color: #1B3C53;
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .stats-grid {
    grid-template-columns: 1fr;
  }
  
  .experience-grid {
    grid-template-columns: 1fr;
  }
  
  .section-title {
    font-size: 2rem;
  }
}
</style>
