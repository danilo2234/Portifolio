<template>
  <div class="portfolio">
    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-container">
        <div class="avatar">DDev</div>
        
        <h1 class="hero-title">Danilo Dev</h1>
        
        <p class="hero-subtitle">Desenvolvedor Full Stack</p>
        
        <p class="hero-tagline">"Transformando ideias em código"</p>
        
        <div class="hero-buttons">
          <a href="#projects" class="btn btn-primary">
            Ver Projetos
          </a>
          <router-link to="/sobre" class="btn btn-secondary">
            Sobre Mim
          </router-link>
        </div>
      </div>
    </section>

    <!-- Introduction Section -->
    <section class="introduction">
      <div class="introduction-container">
        <p class="introduction-text">
          Olá! Sou um desenvolvedor apaixonado por criar experiências digitais incríveis. 
          Especializado em desenvolvimento web moderno, sempre buscando aprender novas tecnologias 
          e aplicar as melhores práticas em meus projetos.
        </p>
        
        <div class="tech-badges">
          <span 
            v-for="tech in technologies" 
            :key="tech.name"
            class="tech-badge"
            :style="{ borderColor: tech.color, color: tech.color }"
          >
            {{ tech.name }}
          </span>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <ProjectsList />

    <!-- Call to Action -->
    <section class="cta">
      <div class="cta-container">
        <h2 class="cta-title">Gostou do meu trabalho?</h2>
        <p class="cta-text">
          Vamos conversar sobre como posso ajudar no seu próximo projeto
        </p>
        <router-link to="/sobre" class="btn btn-cta">Entre em Contato</router-link>
      </div>
    </section>
  </div>
</template>

<script>
import ProjectsList from '@/components/ProjectsList.vue';

export default {
  name: 'PortfolioHome',
  components: {
    ProjectsList
  },
  data() {
    return {
      technologies: [
        { name: "Vue.js", color: "#42b883" },
        { name: "JavaScript", color: "#f7df1e" },
        { name: "HTML5", color: "#e34f26" },
        { name: "CSS3", color: "#1572b6" },
        { name: "Git", color: "#f05032" },
        { name: "API REST", color: "#6366f1" }
      ]
    };
  }
};
</script>

<style scoped>
/* Mantenha apenas os estilos específicos da Home */
.hero {
  padding: 8rem 1rem 5rem;
}

.hero-container {
  max-width: 896px;
  margin: 0 auto;
  text-align: center;
}

.avatar {
  width: 128px;
  height: 128px;
  margin: 0 auto 2rem;
  border-radius: 50%;
  background: linear-gradient(135deg, #3b82f6, #8b5cf6);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 2.5rem;
  font-weight: bold;
  box-shadow: 0 10px 30px rgba(59, 130, 246, 0.3);
}

.hero-title {
  font-size: 3rem;
  font-weight: bold;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, #2563eb, #8b5cf6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-size: 1.5rem;
  color: #64748b;
  margin-bottom: 1rem;
}

.hero-tagline {
  font-size: 1.25rem;
  color: #94a3b8;
  font-style: italic;
  margin-bottom: 2rem;
}

.hero-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  align-items: center;
}

.btn {
  padding: 0.75rem 2rem;
  border-radius: 0.5rem;
  font-weight: 600;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.3s;
  border: none;
  font-size: 1rem;
}

.btn-primary {
  background-color: #2563eb;
  color: white;
  box-shadow: 0 4px 14px rgba(37, 99, 235, 0.4);
}

.btn-primary:hover {
  background-color: #1d4ed8;
  transform: scale(1.05);
}

.btn-secondary {
  background-color: white;
  color: #2563eb;
  border: 2px solid #2563eb;
}

.btn-secondary:hover {
  background-color: #eff6ff;
  transform: scale(1.05);
}

@media (min-width: 640px) {
  .hero-title {
    font-size: 3.75rem;
  }
  
  .hero-buttons {
    flex-direction: row;
    justify-content: center;
  }
}

.introduction {
  padding: 4rem 1rem;
  background-color: white;
}

.introduction-container {
  max-width: 896px;
  margin: 0 auto;
  text-align: center;
}

.introduction-text {
  font-size: 1.125rem;
  color: #334155;
  line-height: 1.7;
  margin-bottom: 2rem;
}

.tech-badges {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

.tech-badge {
  padding: 0.5rem 1rem;
  border: 2px solid;
  border-radius: 9999px;
  font-weight: 600;
  transition: transform 0.3s;
  cursor: pointer;
}

.tech-badge:hover {
  transform: scale(1.1);
}

.cta {
  padding: 5rem 1rem;
  background: linear-gradient(135deg, #2563eb, #8b5cf6);
  color: white;
}

.cta-container {
  max-width: 896px;
  margin: 0 auto;
  text-align: center;
}

.cta-title {
  font-size: 2.5rem;
  font-weight: bold;
  margin-bottom: 1rem;
}

.cta-text {
  font-size: 1.25rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.btn-cta {
  padding: 1rem 2rem;
  background-color: white;
  color: #2563eb;
  border-radius: 0.5rem;
  font-weight: bold;
  font-size: 1.125rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
  display: inline-block;
}

.btn-cta:hover {
  background-color: #f8fafc;
  transform: scale(1.05);
}
</style>