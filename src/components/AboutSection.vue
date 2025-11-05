<template>
  <section id="about" class="about">
    <div class="container">
      <h2 class="section-title">About Me</h2>
      
      <!-- Professional Summary -->
      <div class="professional-summary">
        <div class="summary-icon">
          <i class="fas fa-user-tie"></i>
        </div>
        <div class="summary-content">
          <h3>Professional Summary</h3>
          <p>
            With a solid <strong>five-year tenure in app development</strong>, specializing in 
            end-to-end systems, I bring a dynamic blend of logical, systematic thinking and 
            adaptability to client needs. Renowned for my easy-going demeanor and fast-paced 
            analytical skills, I thrive on challenges and consistently deliver exceptional results.
          </p>
          <p>
            My expertise spans across frontend and backend technologies, with a strong focus 
            on modern frameworks including <strong>Vue.js, React Native, .NET, and Spring Boot</strong>. 
            I'm passionate about clean code, efficient problem-solving, and creating seamless user experiences.
          </p>
          <p>
            Eager for personal growth, I am actively pursuing opportunities to ascend to a 
            <strong>managerial role</strong>, where I can leverage my influence in decision-making 
            processes and drive impactful advancements in system development initiatives.
          </p>
        </div>
      </div>

      <div class="about-content">
        <!-- Stats Section - Full Width -->
        <div class="about-stats">
          <div class="stat">
            <i class="fas fa-calendar-check"></i>
            <h3>8+</h3>
            <p>Years Experience</p>
          </div>
          <div class="stat">
            <i class="fas fa-project-diagram"></i>
            <h3>10+</h3>
            <p>Projects Completed</p>
          </div>
          <div class="stat">
            <i class="fas fa-layer-group"></i>
            <h3>Full-Stack</h3>
            <p>Expertise</p>
          </div>
          <div class="stat">
            <i class="fas fa-award"></i>
            <h3>100%</h3>
            <p>Client Satisfaction</p>
          </div>
        </div>

        <!-- Highlights Section - Full Width -->
        <div class="about-highlights">
          <div class="highlight-card">
            <i class="fas fa-code"></i>
            <h3>Full-Stack Development</h3>
            <p>Expert in building end-to-end solutions with modern tech stacks including Vue.js, React Native, .NET, and Spring Boot</p>
          </div>
          <div class="highlight-card">
            <i class="fas fa-brain"></i>
            <h3>Analytical Problem Solver</h3>
            <p>Fast-paced analytical thinking combined with systematic approach to tackle complex challenges</p>
          </div>
          <div class="highlight-card">
            <i class="fas fa-users-cog"></i>
            <h3>Client-Focused Adaptability</h3>
            <p>Easy-going demeanor with strong adaptability to diverse client needs and project requirements</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Component-specific logic can be added here if needed
</script>

<style scoped>
.about {
  padding: 80px 0;
  background: var(--background-color);
}

/* Professional Summary */
.professional-summary {
  display: flex;
  gap: 25px;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  padding: 35px;
  border-radius: 15px;
  margin-bottom: 60px;
  box-shadow: var(--shadow-lg);
  align-items: flex-start;
}

.summary-icon {
  font-size: 3.5rem;
  color: #ffffff;
  opacity: 0.9;
  min-width: 70px;
  text-align: center;
}

.summary-content h3 {
  color: #ffffff;
  font-size: 1.8rem;
  margin-bottom: 15px;
  font-weight: 700;
}

.summary-content p {
  color: rgba(255, 255, 255, 0.95);
  font-size: 1.1rem;
  line-height: 1.8;
  margin: 0;
}

.about-content {
  display: flex;
  flex-direction: column;
  gap: 40px;
}

.about-text p {
  margin-bottom: 20px;
  font-size: 1.1rem;
  line-height: 1.8;
}

.about-stats {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 25px;
  margin-bottom: 20px;
}

.stat {
  text-align: center;
  padding: 30px 20px;
  background: var(--surface-color);
  border-radius: 15px;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
  border: 2px solid transparent;
}

.stat:hover {
  transform: translateY(-5px);
  box-shadow: var(--shadow-lg);
  border-color: var(--primary-color);
}

.stat i {
  font-size: 2rem;
  color: var(--primary-color);
  margin-bottom: 15px;
  display: block;
}

.stat h3 {
  font-size: 2.5rem;
  color: var(--primary-color);
  margin-bottom: 8px;
  font-weight: 800;
}

.stat p {
  color: var(--text-color);
  font-size: 0.95rem;
  font-weight: 500;
}

.about-highlights {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

.highlight-card {
  background: var(--surface-color);
  padding: 30px;
  border-radius: 15px;
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
  border: 2px solid transparent;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.highlight-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-lg);
  border-color: var(--secondary-color);
}

.highlight-card i {
  font-size: 3rem;
  color: var(--primary-color);
  margin-bottom: 20px;
  display: block;
}

.highlight-card h3 {
  margin-bottom: 12px;
  color: var(--text-color);
  font-size: 1.3rem;
}

.highlight-card p {
  color: var(--text-secondary);
  margin: 0;
  line-height: 1.7;
  font-size: 0.95rem;
}

/* Responsive Design */
@media (max-width: 968px) {
  .about-stats {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }

  .about-highlights {
    grid-template-columns: 1fr;
    gap: 20px;
  }

  .professional-summary {
    flex-direction: column;
    text-align: center;
  }

  .summary-icon {
    margin: 0 auto;
  }
}

@media (max-width: 640px) {
  .about-stats {
    grid-template-columns: 1fr;
    gap: 15px;
  }

  .stat {
    padding: 25px 15px;
  }

  .stat i {
    font-size: 1.5rem;
  }

  .stat h3 {
    font-size: 2rem;
  }

  .professional-summary {
    padding: 25px;
  }

  .summary-content h3 {
    font-size: 1.4rem;
  }

  .summary-content p {
    font-size: 1rem;
  }

  .summary-icon {
    font-size: 2.5rem;
  }
}
</style>
