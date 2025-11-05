<template>
    <section id="skills" class="skills">
        <div class="container">
            <h2 class="section-title">Technical Expertise</h2>

            <!-- Core Technologies -->
            <div class="tech-stack-section">
                <h3 class="subsection-title">
                    <i class="fas fa-code"></i>
                    Core Technologies
                </h3>
                <div class="tech-cards-grid">
                    <div class="tech-card" v-for="tech in coreTechnologies" :key="tech.name">
                        <div class="tech-icon-wrapper">
                            <i :class="tech.icon" class="tech-icon"></i>
                        </div>
                        <div class="tech-content">
                            <h4>{{ tech.name }}</h4>
                            <p class="tech-experience">{{ tech.experience }}</p>
                            <div class="tech-tools">
                                <span v-for="tool in tech.tools" :key="tool" class="tool-tag">{{ tool }}</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Databases & Tools -->
            <div class="databases-section">
                <h3 class="subsection-title">
                    <i class="fas fa-database"></i>
                    Databases & Development Tools
                </h3>
                <div class="databases-grid">
                    <div class="db-card" v-for="db in databases" :key="db.name">
                        <div class="db-icon-wrapper">
                            <i :class="db.icon" class="db-icon"></i>
                        </div>
                        <div class="db-content">
                            <h4>{{ db.name }}</h4>
                            <p>{{ db.description }}</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Professional Skills -->
            <div class="professional-skills">
                <h3 class="subsection-title">
                    <i class="fas fa-briefcase"></i>
                    Professional Skills
                </h3>
                <div class="prof-skills-grid">
                    <div class="prof-skill-card" v-for="skill in professionalSkills" :key="skill.name">
                        <div class="prof-icon-wrapper">
                            <i :class="skill.icon" class="prof-icon"></i>
                        </div>
                        <div class="prof-skill-content">
                            <h4>{{ skill.name }}</h4>
                            <p>{{ skill.description }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

const coreTechnologies = ref([
    {
        name: 'Frontend Development',
        icon: 'fab fa-vuejs',
        experience: '8+ years building responsive web & mobile applications',
        tools: ['Vue.js', 'React Native', 'Flutter', 'JavaScript', 'HTML/CSS']
    },
    {
        name: 'Backend Development',
        icon: 'fab fa-java',
        experience: '8+ years designing scalable server-side solutions',
        tools: ['Java Spring Boot', '.NET', 'C#', 'VB.NET', 'REST API']
    },
    {
        name: 'Full-Stack Projects',
        icon: 'fas fa-layer-group',
        experience: 'End-to-end ERP systems & enterprise applications',
        tools: ['Microservices', 'MVC Architecture', 'API Design', 'System Integration']
    }
])

const databases = ref([
    {
        name: 'PostgreSQL',
        icon: 'fas fa-database',
        description: 'Primary database for modern applications'
    },
    {
        name: 'SQL Server',
        icon: 'fas fa-server',
        description: 'Enterprise database management & optimization'
    },
    {
        name: 'Git & Version Control',
        icon: 'fab fa-git-alt',
        description: 'Source control, collaboration & CI/CD'
    }
])

const professionalSkills = ref([
    {
        name: 'Team Leadership',
        icon: 'fas fa-users-cog',
        description: 'Leading development teams and coordinating project workflows'
    },
    {
        name: 'Client Collaboration',
        icon: 'fas fa-handshake',
        description: 'Understanding business needs and delivering solutions'
    },
    {
        name: 'Problem Solving',
        icon: 'fas fa-lightbulb',
        description: 'Fast-paced analytical thinking for complex challenges'
    },
    {
        name: 'Project Management',
        icon: 'fas fa-tasks',
        description: 'Workload distribution and smooth project progression'
    },
    {
        name: 'Technical Mentoring',
        icon: 'fas fa-chalkboard-teacher',
        description: 'Guiding team members and knowledge sharing'
    },
    {
        name: 'Adaptability',
        icon: 'fas fa-sync-alt',
        description: 'Quickly adapting to diverse client needs and technologies'
    }
])
</script>

<style scoped>
.skills-section {
    padding: 100px 0;
    background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 100%);
    position: relative;
    overflow: hidden;
}

.skills-section::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--primary-color), transparent);
}

.skills-section h2 {
    text-align: center;
    font-size: 2.5em;
    margin-bottom: 20px;
    background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.section-subtitle {
    text-align: center;
    color: #8892b0;
    font-size: 1.1em;
    margin-bottom: 60px;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
}

/* Core Technologies */
.tech-stack-section {
    margin-bottom: 80px;
}

.tech-stack-section h3 {
    font-size: 1.8em;
    margin-bottom: 30px;
    color: var(--primary-color);
    display: flex;
    align-items: center;
    gap: 10px;
}

.tech-stack-section h3 i {
    font-size: 0.9em;
}

.tech-cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 30px;
}

.tech-card {
    background: var(--surface-color);
    border: 2px solid var(--border-color);
    border-radius: 16px;
    padding: 30px;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
}

.tech-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--primary-color), #3B82F6);
    transform: scaleX(0);
    transition: transform 0.3s ease;
}

.tech-card:hover::before {
    transform: scaleX(1);
}

.tech-card:hover {
    transform: translateY(-8px);
    border-color: var(--primary-color);
    box-shadow: var(--shadow-lg);
}

.tech-icon-wrapper {
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, rgba(30, 58, 138, 0.1), rgba(37, 99, 235, 0.05));
    border-radius: 12px;
    border: 2px solid rgba(30, 58, 138, 0.2);
    margin-bottom: 20px;
    transition: all 0.3s ease;
}

.tech-card:hover .tech-icon-wrapper {
    background: linear-gradient(135deg, rgba(30, 58, 138, 0.2), rgba(37, 99, 235, 0.1));
    border-color: var(--primary-color);
    transform: scale(1.1) rotate(-5deg);
}

.tech-icon {
    font-size: 1.8em;
    color: var(--primary-color);
}

.tech-content {
    width: 100%;
}

.tech-card h4 {
    font-size: 1.4em;
    color: var(--text-color);
    margin: 0 0 12px 0;
    font-weight: 700;
}

.tech-card p {
    color: var(--text-secondary);
    margin-bottom: 20px;
    line-height: 1.7;
    font-size: 0.95em;
}

.tech-tools {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
}

.tool-tag {
    padding: 8px 16px;
    background: linear-gradient(135deg, rgba(30, 58, 138, 0.08), rgba(37, 99, 235, 0.05));
    border: 1.5px solid rgba(30, 58, 138, 0.2);
    border-radius: 20px;
    color: var(--primary-color);
    font-size: 0.85em;
    font-weight: 600;
    transition: all 0.2s ease;
}

.tool-tag:hover {
    background: linear-gradient(135deg, rgba(30, 58, 138, 0.15), rgba(37, 99, 235, 0.1));
    border-color: var(--primary-color);
    transform: translateY(-2px);
}

/* Databases & Tools */
.databases-section {
    margin-bottom: 80px;
}

.databases-section h3 {
    font-size: 1.8em;
    margin-bottom: 30px;
    color: var(--secondary-color);
    display: flex;
    align-items: center;
    gap: 10px;
}

.databases-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
}

.db-card {
    background: var(--surface-color);
    border: 2px solid var(--border-color);
    border-radius: 16px;
    padding: 30px;
    display: flex;
    gap: 20px;
    align-items: flex-start;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
}

.db-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--secondary-color), #14B8A6);
    transform: scaleX(0);
    transition: transform 0.3s ease;
}

.db-card:hover::before {
    transform: scaleX(1);
}

.db-card:hover {
    transform: translateY(-8px);
    border-color: var(--secondary-color);
    box-shadow: var(--shadow-lg);
}

.db-icon-wrapper {
    min-width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, rgba(20, 184, 166, 0.1), rgba(16, 185, 129, 0.05));
    border-radius: 12px;
    border: 2px solid rgba(20, 184, 166, 0.2);
    transition: all 0.3s ease;
}

.db-card:hover .db-icon-wrapper {
    background: linear-gradient(135deg, rgba(20, 184, 166, 0.2), rgba(16, 185, 129, 0.1));
    border-color: var(--secondary-color);
    transform: rotate(5deg) scale(1.05);
}

.db-icon {
    font-size: 1.8em;
    color: var(--secondary-color);
}

.db-content {
    flex: 1;
}

.db-content h4 {
    font-size: 1.25em;
    color: var(--text-color);
    margin-bottom: 8px;
    font-weight: 700;
}

.db-content p {
    color: var(--text-secondary);
    line-height: 1.7;
    margin: 0;
    font-size: 0.95em;
}

/* Professional Skills */
.professional-skills {
    margin-bottom: 40px;
}

.professional-skills h3 {
    font-size: 1.8em;
    margin-bottom: 30px;
    color: var(--accent-color);
    display: flex;
    align-items: center;
    gap: 10px;
}

.prof-skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 25px;
}

.prof-skill-card {
    background: var(--surface-color);
    border: 2px solid var(--border-color);
    border-radius: 16px;
    padding: 30px;
    display: flex;
    gap: 20px;
    align-items: flex-start;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
}

.prof-skill-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, var(--accent-color), #fbbf24);
    transform: scaleX(0);
    transition: transform 0.3s ease;
}

.prof-skill-card:hover::before {
    transform: scaleX(1);
}

.prof-skill-card:hover {
    transform: translateY(-8px);
    border-color: var(--accent-color);
    box-shadow: var(--shadow-lg);
}

.prof-icon-wrapper {
    min-width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, rgba(245, 158, 11, 0.1), rgba(251, 191, 36, 0.05));
    border-radius: 12px;
    border: 2px solid rgba(245, 158, 11, 0.2);
    transition: all 0.3s ease;
}

.prof-skill-card:hover .prof-icon-wrapper {
    background: linear-gradient(135deg, rgba(245, 158, 11, 0.2), rgba(251, 191, 36, 0.1));
    border-color: var(--accent-color);
    transform: rotate(-5deg) scale(1.05);
}

.prof-icon {
    font-size: 1.8em;
    color: var(--accent-color);
}

.prof-skill-content {
    flex: 1;
}

.prof-skill-content h4 {
    font-size: 1.25em;
    color: var(--text-color);
    margin-bottom: 8px;
    font-weight: 700;
}

.prof-skill-content p {
    color: var(--text-secondary);
    line-height: 1.7;
    margin: 0;
    font-size: 0.95em;
}

/* Responsive */
@media (max-width: 768px) {
    .skills-section {
        padding: 60px 0;
    }

    .skills-section h2 {
        font-size: 2em;
    }

    .section-subtitle {
        font-size: 1em;
        margin-bottom: 40px;
    }

    .tech-stack-section,
    .databases-section,
    .professional-skills {
        margin-bottom: 50px;
    }

    .tech-stack-section h3,
    .databases-section h3,
    .professional-skills h3 {
        font-size: 1.5em;
    }

    .tech-cards-grid,
    .databases-grid,
    .prof-skills-grid {
        grid-template-columns: 1fr;
        gap: 20px;
    }

    .tech-card,
    .db-card,
    .prof-skill-card {
        padding: 20px;
    }

    .tech-icon-wrapper {
        width: 50px;
        height: 50px;
        margin-bottom: 15px;
    }

    .tech-icon {
        font-size: 1.5em;
    }

    .tech-card h4 {
        font-size: 1.2em;
    }

    .tech-card p {
        font-size: 0.9em;
    }

    .tool-tag {
        font-size: 0.8em;
        padding: 6px 12px;
    }

    .db-icon-wrapper {
        min-width: 50px;
        height: 50px;
    }

    .db-icon {
        font-size: 1.5em;
    }

    .db-content h4 {
        font-size: 1.1em;
    }

    .db-content p {
        font-size: 0.9em;
    }

    .prof-skill-card {
        padding: 25px;
    }

    .prof-icon-wrapper {
        min-width: 50px;
        height: 50px;
    }

    .prof-icon {
        font-size: 1.5em;
    }

    .prof-skill-content h4 {
        font-size: 1.1em;
    }

    .prof-skill-content p {
        font-size: 0.9em;
    }
}
</style>
