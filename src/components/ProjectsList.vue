<template>
  <section id="projects" class="projects">
    <div class="projects-container">
      <h2 class="section-title">Meus Projetos</h2>
      <p class="section-subtitle">Confira alguns dos meus trabalhos recentes</p>
      
      <div v-if="loading" class="loading">
        Carregando projetos...
      </div>
      
      <div v-else-if="filteredProjects.length === 0" class="no-projects">
        Nenhum projeto encontrado.
      </div>
      
      <div v-else class="projects-grid">
        <ProjectCard 
          v-for="project in filteredProjects" 
          :key="project.id"
          :project="project"
        />
      </div>
      
      <div v-if="hasMoreProjects" class="load-more">
        <button @click="loadMore" class="btn btn-secondary">
          Carregar Mais Projetos
        </button>
      </div>
    </div>
  </section>
</template>

<script>
import { projects } from '@/data/projects.js';
import ProjectCard from './ProjectCard.vue';

export default {
  name: 'ProjectsList',
  components: {
    ProjectCard
  },
  props: {
    featuredOnly: {
      type: Boolean,
      default: false
    },
    limit: {
      type: Number,
      default: null
    }
  },
  data() {
    return {
      allProjects: projects,
      visibleProjects: this.limit || 6,
      loading: false
    };
  },
  computed: {
    filteredProjects() {
      let filtered = this.allProjects;
      
      if (this.featuredOnly) {
        filtered = filtered.filter(project => project.featured);
      }
      
      return filtered.slice(0, this.visibleProjects);
    },
    hasMoreProjects() {
      const total = this.featuredOnly 
        ? this.allProjects.filter(p => p.featured).length 
        : this.allProjects.length;
      
      return this.visibleProjects < total;
    }
  },
  methods: {
    loadMore() {
      this.visibleProjects += 3;
    }
  }
};
</script>

<style scoped>
.projects {
  padding: 5rem 1rem;
  background-color: #f8fafc;
}

.projects-container {
  max-width: 1280px;
  margin: 0 auto;
}

.section-title {
  font-size: 2.5rem;
  font-weight: bold;
  text-align: center;
  margin-bottom: 1rem;
  color: #0f172a;
}

.section-subtitle {
  text-align: center;
  color: #64748b;
  margin-bottom: 3rem;
  font-size: 1.125rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 2rem;
}

.loading, .no-projects {
  text-align: center;
  padding: 3rem;
  color: #64748b;
  font-size: 1.125rem;
}

.load-more {
  text-align: center;
  margin-top: 3rem;
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
  background-color: white;
  color: #2563eb;
  border: 2px solid #2563eb;
}

.btn:hover {
  background-color: #eff6ff;
  transform: scale(1.05);
}

@media (min-width: 640px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 768px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>