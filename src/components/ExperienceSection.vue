<template>
    <section id="experience" class="experience">
        <div class="container">
            <h2 class="section-title">Professional Experience</h2>

            <!-- Featured Freelance Project -->
            <div class="featured-project">
                <h3 class="subsection-title">
                    <i class="fas fa-star"></i>
                    Featured Freelance Project
                </h3>
                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">
                            <h4>Enterprise Resource Planning (ERP) System</h4>
                            <span class="project-badge">Full-Stack Development</span>
                        </div>
                        <div class="tech-stack-mini">
                            <span class="tech-tag">Flutter</span>
                            <span class="tech-tag">Java Spring Boot</span>
                            <span class="tech-tag">PostgreSQL</span>
                        </div>
                    </div>
                    <div class="project-body">
                        <p class="project-description">
                            Developed a comprehensive web-based ERP solution for a corporate client, managing
                            end-to-end business operations with a modern, scalable architecture.
                        </p>
                        <div class="project-features">
                            <div class="feature-grid">
                                <div class="feature-item">
                                    <i class="fas fa-chart-line"></i>
                                    <span>Interactive Dashboard & Analytics</span>
                                </div>
                                <div class="feature-item">
                                    <i class="fas fa-shopping-cart"></i>
                                    <span>Order Management System</span>
                                </div>
                                <div class="feature-item">
                                    <i class="fas fa-users"></i>
                                    <span>Customer Relationship Management</span>
                                </div>
                                <div class="feature-item">
                                    <i class="fas fa-boxes"></i>
                                    <span>Inventory Control & Tracking</span>
                                </div>
                                <div class="feature-item">
                                    <i class="fas fa-dollar-sign"></i>
                                    <span>Financial Management</span>
                                </div>
                                <div class="feature-item">
                                    <i class="fas fa-book"></i>
                                    <span>Journal Entry & Reporting</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- All Experiences -->
            <h3 class="subsection-title">
                <i class="fas fa-briefcase"></i>
                Work History
            </h3>
            <div class="experiences-grid">
                <div class="experience-card" v-for="(exp, index) in experiences" :key="index">
                    <div class="card-header">
                        <div class="card-title">
                            <h4>{{ exp.title }}</h4>
                            <span v-if="exp.badge" class="experience-badge">{{ exp.badge }}</span>
                        </div>
                        <p class="company">
                            <i class="fas fa-building"></i>
                            {{ exp.company }}
                        </p>
                        <p class="period">
                            <i class="fas fa-calendar-alt"></i>
                            {{ exp.period }}
                        </p>
                    </div>
                    <div class="card-body">
                        <ul class="highlights-list">
                            <li v-for="(item, idx) in exp.highlights" :key="idx">
                                <i class="fas fa-check-circle"></i>
                                <span>{{ item }}</span>
                            </li>
                        </ul>
                        <div v-if="exp.technologies" class="tech-tags">
                            <span v-for="tech in exp.technologies" :key="tech" class="tech-tag">{{ tech }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

const experiences = ref([
    {
        title: 'Team Leader',
        company: 'ADIRA Finance',
        period: '2022 - Now',
        badge: 'Leadership',
        highlights: [
            'Collaborating with users to discuss and analyze evolving business needs',
            'Managing development teams and coordinating workload distribution',
            'Resolving technical issues and ensuring smooth project progression',
            'Hands-on full-stack development for internal office applications',
            'Leading technical decisions and architectural planning'
        ],
        technologies: ['Vue.js', 'React Native', '.NET', 'Spring Boot', 'PostgreSQL', 'Flutter','Node JS','Agile Methodology','Waterfall' , 'Jira','Bitbucket','Confluence']
    },
    {
        title: 'Senior Developer',
        company: 'ADIRA Finance',
        period: '2020 - 2022',
        highlights: [
            'Developed sophisticated websites and mobile applications',
            'Leveraged cutting-edge technologies for frontend and backend requirements',
            'Built responsive mobile applications using Flutter framework',
            'Designed and implemented backend operations with Java Spring Boot',
            'Managed efficient database solutions using PostgreSQL',
            'Delivered seamless user experiences across web and mobile platforms'
        ],
        technologies: ['Flutter', 'Java Spring Boot', 'PostgreSQL']
    },
    {
        title: 'Middle Developer',
        company: 'ADIRA Finance',
        period: '2019 - 2020',
        highlights: [
            'Managed website development projects with full project lifecycle',
            'Developed sophisticated data-driven online platforms',
            'Built robust applications using C# programming language',
            'Implemented SQL Server for efficient database management',
            'Ensured seamless functionality and optimal user engagement',
            'Delivered dynamic web solutions for finance operations'
        ],
        technologies: ['C#', 'SQL Server', 'ASP.NET']
    },
    {
        title: 'Junior Developer',
        company: 'PT Success Integrity Solution',
        period: '2018 - 2019',
        highlights: [
            'Prioritized meeting client needs by crafting ERP-based systems',
            'Developed robust applications using .NET and VB.NET frameworks',
            'Managed SQL Server databases ensuring optimal performance',
            'Ensured seamless system functionality and robust database management',
            'Proactively engaged with corporate clients for smooth operations',
            'Built enduring client relationships through excellent project delivery'
        ],
        technologies: ['.NET', 'VB.NET', 'SQL Server']
    }
])
</script>

<style scoped>
.experience {
    padding: 80px 0;
    background: var(--surface-color);
    transition: background-color 0.3s ease;
}

/* Featured Project Section */
.featured-project {
    margin-bottom: 60px;
}

.subsection-title {
    font-size: 1.8rem;
    color: var(--text-color);
    margin-bottom: 30px;
    display: flex;
    align-items: center;
    gap: 12px;
}

.subsection-title i {
    color: var(--accent-color);
    font-size: 1.6rem;
}

.project-card {
    background: linear-gradient(135deg, rgba(30, 58, 138, 0.05), rgba(20, 184, 166, 0.05));
    border-radius: 15px;
    padding: 35px;
    box-shadow: var(--shadow-lg);
    border: 2px solid var(--primary-color);
    transition: all 0.3s ease;
}

.project-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 25px 35px -5px rgba(30, 58, 138, 0.2), 0 15px 15px -5px rgba(30, 58, 138, 0.1);
    border-color: var(--secondary-color);
}

.project-header {
    margin-bottom: 25px;
}

.project-title {
    display: flex;
    align-items: center;
    gap: 15px;
    margin-bottom: 15px;
    flex-wrap: wrap;
}

.project-title h4 {
    font-size: 1.6rem;
    color: var(--text-color);
    margin: 0;
}

.project-badge {
    background: linear-gradient(135deg, var(--accent-color), #F97316);
    color: white;
    padding: 6px 16px;
    border-radius: 20px;
    font-size: 0.85rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    box-shadow: 0 4px 10px rgba(245, 158, 11, 0.3);
}

.tech-stack-mini {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
}

.tech-tag {
    background: var(--background-color);
    color: var(--primary-color);
    padding: 8px 16px;
    border-radius: 8px;
    font-size: 0.9rem;
    font-weight: 600;
    border: 2px solid var(--border-color);
    transition: all 0.2s ease;
}

.tech-tag:hover {
    border-color: var(--primary-color);
    background: var(--primary-color);
    color: white;
    transform: translateY(-2px);
}

.project-body {
    margin-top: 20px;
}

.project-description {
    font-size: 1.05rem;
    line-height: 1.8;
    color: var(--text-color);
    margin-bottom: 25px;
}

.project-features {
    margin-top: 25px;
}

.feature-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 15px;
}

.feature-item {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px 16px;
    background: var(--surface-color);
    border-radius: 8px;
    transition: all 0.3s ease;
    border: 1px solid var(--border-color);
}

.feature-item:hover {
    background: var(--primary-color);
    color: white;
    transform: translateX(5px);
    border-color: var(--primary-color);
}

.feature-item i {
    color: var(--secondary-color);
    font-size: 1.2rem;
    min-width: 20px;
    transition: color 0.3s ease;
}

.feature-item:hover i {
    color: var(--accent-color);
}

.feature-item span {
    font-size: 0.95rem;
    font-weight: 500;
}

/* Experiences Grid */
.experiences-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 30px;
    margin-top: 40px;
}

.experience-card {
    background: var(--surface-color);
    border-radius: 15px;
    padding: 30px;
    box-shadow: var(--shadow-lg);
    border: 2px solid var(--border-color);
    transition: all 0.3s ease;
    display: flex;
    flex-direction: column;
}

.experience-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 25px 35px -5px rgba(30, 58, 138, 0.2), 0 15px 15px -5px rgba(30, 58, 138, 0.1);
    border-color: var(--primary-color);
}

.card-header {
    margin-bottom: 20px;
    border-bottom: 2px solid var(--border-color);
    padding-bottom: 15px;
}

.card-title {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    margin-bottom: 12px;
    flex-wrap: wrap;
}

.card-title h4 {
    font-size: 1.4rem;
    color: var(--text-color);
    margin: 0;
    flex: 1;
    min-width: 200px;
}

.experience-badge {
    background: linear-gradient(135deg, var(--secondary-color), #059669);
    color: white;
    padding: 4px 12px;
    border-radius: 15px;
    font-size: 0.75rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    text-transform: uppercase;
}

.card-header .company {
    color: var(--primary-color);
    font-weight: 600;
    font-size: 1.05rem;
    margin-bottom: 8px;
    display: flex;
    align-items: center;
    gap: 8px;
}

.card-header .company i {
    font-size: 0.9rem;
}

.card-header .period {
    color: var(--text-secondary);
    font-size: 0.9rem;
    display: flex;
    align-items: center;
    gap: 8px;
}

.card-header .period i {
    font-size: 0.85rem;
}

.card-body {
    flex: 1;
}

.highlights-list {
    list-style: none;
    margin: 0;
    padding: 0;
}

.highlights-list li {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    margin-bottom: 12px;
    color: var(--text-color);
    line-height: 1.6;
}

.highlights-list li i {
    color: var(--secondary-color);
    font-size: 0.9rem;
    margin-top: 4px;
    flex-shrink: 0;
}

.highlights-list li span {
    flex: 1;
}

.card-body .tech-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 20px;
    padding-top: 15px;
    border-top: 1px solid var(--border-color);
}

.card-body .tech-tag {
    background: var(--background-color);
    color: var(--primary-color);
    padding: 6px 14px;
    border-radius: 8px;
    font-size: 0.85rem;
    font-weight: 600;
    border: 2px solid var(--border-color);
    transition: all 0.2s ease;
}

.card-body .tech-tag:hover {
    border-color: var(--primary-color);
    background: var(--primary-color);
    color: white;
    transform: translateY(-2px);
}

@media (max-width: 968px) {
    .feature-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .experiences-grid {
        grid-template-columns: 1fr;
    }
}

@media (max-width: 640px) {
    .feature-grid {
        grid-template-columns: 1fr;
    }

    .experiences-grid {
        grid-template-columns: 1fr;
    }

    .project-card {
        padding: 25px;
    }

    .experience-card {
        padding: 20px;
    }

    .card-title h4 {
        font-size: 1.2rem;
    }

    .project-title {
        flex-direction: column;
        align-items: flex-start;
    }

    .project-title h4 {
        font-size: 1.3rem;
    }

    .subsection-title {
        font-size: 1.5rem;
    }
}

@media (prefers-color-scheme: dark) {
    .project-card {
        background: linear-gradient(135deg, rgba(37, 99, 235, 0.05), rgba(16, 185, 129, 0.05));
    }
}
</style>
