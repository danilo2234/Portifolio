<template>
  <article class="project-card">
    <img 
      :src="project.image" 
      :alt="project.title"
      class="project-image"
    />
    
    <div class="project-content">
      <h3 class="project-title">{{ project.title }}</h3>
      <p class="project-description">{{ project.description }}</p>
      
      <div class="project-tech">
        <span 
          v-for="tech in project.technologies" 
          :key="tech"
          class="tech-tag"
        >
          {{ tech }}
        </span>
      </div>
      
      <div class="project-buttons">
        <a 
          :href="project.github" 
          target="_blank"
          rel="noopener noreferrer"
          class="project-btn btn-github"
          title="Ver código no GitHub"
        >
          <span class="btn-icon">💻</span>
          <span class="btn-text">Código</span>
        </a>
        <a 
          v-if="project.demo"
          :href="project.demo" 
          target="_blank"
          rel="noopener noreferrer"
          class="project-btn btn-demo"
          title="Ver demonstração"
        >
          <span class="btn-icon">🚀</span>
          <span class="btn-text">Demo</span>
        </a>
        <button 
          v-else
          class="project-btn btn-disabled"
          disabled
          title="Demo não disponível"
        >
          <span class="btn-icon">🔒</span>
          <span class="btn-text">Demo</span>
        </button>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: 'ProjectCard',
  props: {
    project: {
      type: Object,
      required: true
    }
  }
};
</script>

<style scoped>
.project-card {
  background-color: white;
  border-radius: 0.75rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: all 0.3s;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.project-card:hover {
  box-shadow: 0 20px 25px rgba(0, 0, 0, 0.15);
  transform: translateY(-8px);
}

.project-image {
  width: 100%;
  height: 192px;
  object-fit: cover;
  display: block;
}

.project-content {
  padding: 1.5rem;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.project-title {
  font-size: 1.25rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
  color: #0f172a;
}

.project-description {
  color: #64748b;
  margin-bottom: 1rem;
  line-height: 1.5;
  flex-grow: 1;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.tech-tag {
  padding: 0.25rem 0.75rem;
  background-color: #dbeafe;
  color: #2563eb;
  border-radius: 9999px;
  font-size: 0.75rem;
  font-weight: 500;
  white-space: nowrap;
}

.project-buttons {
  display: flex;
  gap: 0.75rem;
  margin-top: auto;
}

.project-btn {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.3s;
  border: none;
  cursor: pointer;
  font-size: 0.875rem;
}

.btn-github {
  background-color: #1e293b;
  color: white;
}

.btn-github:hover {
  background-color: #0f172a;
  transform: scale(1.05);
}

.btn-demo {
  background-color: #2563eb;
  color: white;
}

.btn-demo:hover {
  background-color: #1d4ed8;
  transform: scale(1.05);
}

.btn-disabled {
  background-color: #e2e8f0;
  color: #94a3b8;
  cursor: not-allowed;
}

.btn-disabled:hover {
  transform: none;
  background-color: #e2e8f0;
}

.btn-icon {
  font-size: 1rem;
}

@media (max-width: 640px) {
  .btn-text {
    display: none;
  }
  
  .project-btn {
    padding: 0.5rem;
  }
}
</style>