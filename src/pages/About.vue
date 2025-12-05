<template>
  <div class="about-page">
    <!-- Hero Section -->
    <section class="about-hero">
      <div class="about-hero-container">
        <div class="about-avatar">DDev</div>
        
        <h1 class="about-title">Sobre Mim</h1>
        
        <p class="about-subtitle">
          Desenvolvedor Full Stack • Apaixonado por Tecnologia • Resolvedor de Problemas
        </p>
      </div>
    </section>

    <!-- Story Section -->
    <section class="story-section">
      <div class="container">
        <h2 class="section-title">Minha Jornada</h2>
        <div class="story-content">
          <p>
            Minha paixão por tecnologia começou quando criança, ao desmontar e montar computadores.
            Com o tempo, essa curiosidade evoluiu para a programação, onde descobri a magia de criar
            soluções digitais que impactam positivamente a vida das pessoas.
          </p>
          <p>
            Formado em Informática para Internet pela Etec Antônio Furlan, sempre buscando aprender novas tecnologias e metodologias.
            Acredito no poder da educação contínua e no compartilhamento de conhecimento.
          </p>
          <p>
            Meu objetivo é criar software que não apenas funcione bem, mas que também proporcione
            experiências excepcionais para os usuários.
          </p>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section class="skills-section">
      <div class="container">
        <h2 class="section-title">Minhas Habilidades</h2>
        
        <div class="skills-grid">
          <!-- Hard Skills -->
          <div class="skills-category">
            <h3 class="skills-category-title">
              <span class="skills-icon">💻</span> Hard Skills
            </h3>
            <ul class="skills-list">
              <li 
                v-for="skill in hardSkills" 
                :key="skill.name"
                class="skill-item"
              >
                <div class="skill-info">
                  <span class="skill-name">{{ skill.name }}</span>
                  <span class="skill-level">{{ skill.level }}</span>
                </div>
                <div class="skill-bar">
                  <div 
                    class="skill-progress" 
                    :style="{ width: skill.percentage + '%', backgroundColor: skill.color }"
                  ></div>
                </div>
              </li>
            </ul>
          </div>

          <!-- Soft Skills -->
          <div class="skills-category">
            <h3 class="skills-category-title">
              <span class="skills-icon">🧠</span> Soft Skills
            </h3>
            <div class="soft-skills">
              <span 
                v-for="skill in softSkills" 
                :key="skill"
                class="soft-skill-tag"
              >
                {{ skill }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>


    <!-- Contact Section -->
    <section class="contact-section">
      <div class="container">
        <h2 class="section-title">Vamos Conversar!</h2>
        
        <div class="contact-grid">
          <div class="contact-info">
            <h3 class="contact-subtitle">Informações de Contato</h3>
            
            <div class="contact-item">
              <span class="contact-icon">📧</span>
              <div>
                <p class="contact-label">Email</p>
                <a href="mailto:francodanilo80@gmail.com" class="contact-value">
                  francodanilo80@gmail.com
                </a>
              </div>
            </div>
            
            <div class="contact-item">
              <span class="contact-icon">💼</span>
              <div>
                <p class="contact-label">LinkedIn</p>
                <a 
                  href="https://linkedin.com/in/danilomlf" 
                  target="_blank"
                  rel="noopener noreferrer"
                  class="contact-value"
                >
                  linkedin.com/in/danilomlf
                </a>
              </div>
            </div>
            
            <div class="contact-item">
              <span class="contact-icon">🐙</span>
              <div>
                <p class="contact-label">GitHub</p>
                <a 
                  href="https://github.com/danilo2234" 
                  target="_blank"
                  rel="noopener noreferrer"
                  class="contact-value"
                >
                  github.com/danilo2234
                </a>
              </div>
            </div>
          </div>
          
          <div class="contact-form">
            <h3 class="contact-subtitle">Envie uma Mensagem</h3>
            
            <form @submit.prevent="submitContact" class="form">
              <div class="form-group">
                <label for="name" class="form-label">Nome</label>
                <input
                  id="name"
                  v-model="contactForm.name"
                  type="text"
                  class="form-input"
                  required
                />
              </div>
              
              <div class="form-group">
                <label for="email" class="form-label">Email</label>
                <input
                  id="email"
                  v-model="contactForm.email"
                  type="email"
                  class="form-input"
                  required
                />
              </div>
              
              <div class="form-group">
                <label for="message" class="form-label">Mensagem</label>
                <textarea
                  id="message"
                  v-model="contactForm.message"
                  rows="5"
                  class="form-textarea"
                  required
                ></textarea>
              </div>
              
              <button type="submit" class="btn btn-primary" :disabled="submitting">
                {{ submitting ? 'Enviando...' : 'Enviar Mensagem' }}
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Featured Projects -->
    <section class="featured-projects">
      <div class="container">
        <h2 class="section-title">Projetos em Destaque</h2>
        <ProjectsList :featured-only="true" :limit="3" />
      </div>
    </section>
  </div>
</template>

<script>
import ProjectsList from '@/components/ProjectsList.vue';

export default {
  name: 'AboutPage',
  components: {
    ProjectsList
  },
  data() {
    return {
      hardSkills: [
        { name: 'Vue.js', level: 'Avançado', percentage: 85, color: '#42b883' },
        { name: 'JavaScript', level: 'Avançado', percentage: 75, color: '#f7df1e' },
        { name: 'HTML/CSS', level: 'Avançado', percentage: 95, color: '#e34f26' },
        { name: 'React', level: 'Intermediário', percentage: 60, color: '#61dafb' },
        { name: 'Node.js', level: 'Intermediário', percentage: 65, color: '#339933' },
        { name: 'Git', level: 'Avançado', percentage: 85, color: '#f05032' },
        { name: 'API REST', level: 'Intermediário', percentage: 60, color: '#6366f1' },
        { name: 'TypeScript', level: 'Intermediário', percentage: 55, color: '#3178c6' }
      ],
      softSkills: [
        'Comunicação',
        'Trabalho em Equipe',
        'Resolução de Problemas',
        'Gestão de Tempo',
        'Adaptabilidade',
        'Pensamento Crítico',
        'Empatia',
        'Liderança'
      ],
      contactForm: {
        name: '',
        email: '',
        message: ''
      },
      submitting: false
    };
  },
  methods: {
    async submitContact() {
      this.submitting = true;
      
      // Simulação de envio
      await new Promise(resolve => setTimeout(resolve, 1500));
      
      alert('Mensagem enviada com sucesso! Entrarei em contato em breve.');
      
      // Reset form
      this.contactForm = {
        name: '',
        email: '',
        message: ''
      };
      
      this.submitting = false;
    }
  }
};
</script>

<style scoped>
.about-page {
  padding-top: 64px;
  background-color: #f8fafc;
  min-height: 100vh;
}

/* Common */
.container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 1rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: bold;
  text-align: center;
  margin-bottom: 3rem;
  color: #0f172a;
}

/* Hero Section */
.about-hero {
  padding: 4rem 1rem;
  background: linear-gradient(135deg, #2563eb, #8b5cf6);
  color: white;
  text-align: center;
}

.about-hero-container {
  max-width: 896px;
  margin: 0 auto;
}

.about-avatar {
  width: 96px;
  height: 96px;
  margin: 0 auto 1.5rem;
  border-radius: 50%;
  background: linear-gradient(135deg, #3b82f6, #a78bfa);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 2rem;
  font-weight: bold;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

.about-title {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.about-subtitle {
  font-size: 1.25rem;
  opacity: 0.9;
}

/* Story Section */
.story-section {
  padding: 5rem 1rem;
  background-color: white;
}

.story-content {
  max-width: 768px;
  margin: 0 auto;
  font-size: 1.125rem;
  line-height: 1.8;
  color: #334155;
}

.story-content p {
  margin-bottom: 1.5rem;
}

/* Skills Section */
.skills-section {
  padding: 5rem 1rem;
  background-color: #f1f5f9;
}

.skills-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3rem;
  max-width: 1024px;
  margin: 0 auto;
}

.skills-category-title {
  font-size: 1.5rem;
  margin-bottom: 1.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.skills-icon {
  font-size: 1.5rem;
}

.skills-list {
  list-style: none;
}

.skill-item {
  margin-bottom: 1.5rem;
}

.skill-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
}

.skill-name {
  font-weight: 600;
  color: #334155;
}

.skill-level {
  color: #64748b;
  font-size: 0.875rem;
}

.skill-bar {
  height: 8px;
  background-color: #e2e8f0;
  border-radius: 4px;
  overflow: hidden;
}

.skill-progress {
  height: 100%;
  border-radius: 4px;
  transition: width 1s ease-in-out;
}

.soft-skills {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.soft-skill-tag {
  padding: 0.5rem 1rem;
  background-color: white;
  color: #2563eb;
  border-radius: 9999px;
  font-weight: 500;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.soft-skill-tag:hover {
  transform: translateY(-2px);
}

@media (min-width: 768px) {
  .skills-grid {
    grid-template-columns: 1fr 1fr;
  }
}

/* Experience Section */
.experience-section {
  padding: 5rem 1rem;
  background-color: white;
}

.timeline {
  position: relative;
  max-width: 768px;
  margin: 0 auto;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: 2px;
  background-color: #e2e8f0;
  transform: translateX(-50%);
}

.timeline-item {
  position: relative;
  margin-bottom: 3rem;
}

.timeline-content {
  background-color: white;
  border-radius: 0.75rem;
  padding: 1.5rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  border: 1px solid #e2e8f0;
  position: relative;
}

.timeline-title {
  font-size: 1.25rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
  color: #0f172a;
}

.timeline-company {
  color: #2563eb;
  font-weight: 600;
  margin-bottom: 0.25rem;
}

.timeline-period {
  color: #64748b;
  font-size: 0.875rem;
  margin-bottom: 0.75rem;
}

.timeline-description {
  color: #334155;
  line-height: 1.6;
  margin-bottom: 1rem;
}

.timeline-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.timeline-tech-tag {
  padding: 0.25rem 0.75rem;
  background-color: #dbeafe;
  color: #2563eb;
  border-radius: 9999px;
  font-size: 0.75rem;
  font-weight: 500;
}

@media (min-width: 768px) {
  .timeline-item {
    width: calc(50% - 2rem);
  }
  
  .timeline-item:nth-child(odd) {
    margin-right: calc(50% + 2rem);
  }
  
  .timeline-item:nth-child(even) {
    margin-left: calc(50% + 2rem);
  }
}

@media (max-width: 767px) {
  .timeline::before {
    left: 1rem;
  }
  
  .timeline-item {
    margin-left: 2rem;
  }
}

/* Contact Section */
.contact-section {
  padding: 5rem 1rem;
  background-color: #f1f5f9;
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 3rem;
  max-width: 1024px;
  margin: 0 auto;
}

.contact-subtitle {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 1.5rem;
  color: #0f172a;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  margin-bottom: 1.5rem;
  padding: 1rem;
  background-color: white;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.contact-icon {
  font-size: 1.5rem;
}

.contact-label {
  font-size: 0.875rem;
  color: #64748b;
  margin-bottom: 0.25rem;
}

.contact-value {
  color: #2563eb;
  text-decoration: none;
  font-weight: 500;
  word-break: break-all;
}

.contact-value:hover {
  text-decoration: underline;
}

.form {
  background-color: white;
  padding: 2rem;
  border-radius: 0.75rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.form-group {
  margin-bottom: 1.5rem;
}

.form-label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
  color: #334155;
}

.form-input,
.form-textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #cbd5e1;
  border-radius: 0.5rem;
  font-size: 1rem;
  transition: border-color 0.3s;
}

.form-input:focus,
.form-textarea:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
}

.form-textarea {
  resize: vertical;
  min-height: 100px;
}

.btn {
  padding: 0.75rem 2rem;
  border-radius: 0.5rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
  border: none;
  font-size: 1rem;
}

.btn-primary {
  background-color: #2563eb;
  color: white;
  width: 100%;
}

.btn-primary:hover:not(:disabled) {
  background-color: #1d4ed8;
  transform: scale(1.02);
}

.btn-primary:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

@media (min-width: 768px) {
  .contact-grid {
    grid-template-columns: 1fr 1fr;
  }
  
  .btn-primary {
    width: auto;
  }
}

/* Featured Projects */
.featured-projects {
  padding: 5rem 1rem;
  background-color: white;
}
</style>