<template>
  <footer class="footer">
    <div class="footer-container">
      <div class="social-links">
        <a 
          href="https://github.com/danilo2234" 
          target="_blank"
          rel="noopener noreferrer"
          class="social-link"
          title="GitHub"
        >
          <span class="social-icon">🐙</span>
          GitHub
        </a>
        <a 
          href="https://linkedin.com/in/danilomlf" 
          target="_blank"
          rel="noopener noreferrer"
          class="social-link"
          title="LinkedIn"
        >
          <span class="social-icon">💼</span>
          LinkedIn
        </a>
        <a 
          href="mailto:francodanilo80@gmail.com"
          class="social-link"
          title="Email"
        >
          <span class="social-icon">✉️</span>
          Email
        </a>
        <a 
          href="https://twitter.com/Dscoppl" 
          target="_blank"
          rel="noopener noreferrer"
          class="social-link"
          title="Twitter"
        >
          <span class="social-icon">🐦</span>
          X
        </a>
      </div>
      
      <p class="copyright">
        © {{ currentYear }} Danilo Development - Todos os direitos reservados
      </p>
      
      <button @click="scrollToTop" class="back-to-top">
        ↑ Voltar ao topo
      </button>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'AppFooter',
  data() {
    return {
      currentYear: new Date().getFullYear()
    };
  },
  methods: {
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }
  }
};
</script>

<style scoped>
.footer {
  background-color: #1e293b;
  color: white;
  padding: 3rem 1rem;
}

.footer-container {
  max-width: 1280px;
  margin: 0 auto;
  text-align: center;
}

.social-links {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.social-link {
  color: white;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  transition: all 0.3s;
  background-color: rgba(255, 255, 255, 0.1);
}

.social-link:hover {
  background-color: rgba(255, 255, 255, 0.2);
  transform: translateY(-2px);
}

.social-icon {
  font-size: 1.25rem;
}

.copyright {
  text-align: center;
  color: #94a3b8;
  margin-bottom: 1.5rem;
  font-size: 0.875rem;
}

.back-to-top {
  display: block;
  margin: 0 auto;
  background: none;
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #60a5fa;
  cursor: pointer;
  font-size: 0.875rem;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  transition: all 0.3s;
}

.back-to-top:hover {
  background-color: rgba(96, 165, 250, 0.1);
  border-color: #60a5fa;
}
</style>