<template>
  <header class="header">
    <div class="header-container">
      <div class="header-content">
        <router-link to="/" class="logo">
          MeuPortfólio
        </router-link>
        
        <!-- Desktop Menu -->
        <nav class="nav-desktop">
          <router-link 
            to="/" 
            class="nav-link"
            :class="{ 'active': $route.path === '/' }"
          >
            Home
          </router-link>
          <router-link 
            to="/sobre" 
            class="nav-link"
            :class="{ 'active': $route.path === '/sobre' }"
          >
            Sobre
          </router-link>
          <a href="#projects" class="nav-link">Projetos</a>
        </nav>

        <!-- Mobile Menu Button -->
        <button class="menu-button" @click="toggleMenu">
          <span v-if="!menuOpen">☰</span>
          <span v-else>✕</span>
        </button>
      </div>

      <!-- Mobile Menu -->
      <nav v-if="menuOpen" class="nav-mobile">
        <router-link 
          to="/" 
          class="nav-link"
          :class="{ 'active': $route.path === '/' }"
          @click="closeMenu"
        >
          Home
        </router-link>
        <router-link 
          to="/sobre" 
          class="nav-link"
          :class="{ 'active': $route.path === '/sobre' }"
          @click="closeMenu"
        >
          Sobre
        </router-link>
        <a href="#projects" class="nav-link" @click="closeMenu">Projetos</a>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
  data() {
    return {
      menuOpen: false
    };
  },
  methods: {
    toggleMenu() {
      this.menuOpen = !this.menuOpen;
    },
    closeMenu() {
      this.menuOpen = false;
    }
  },
  watch: {
    $route() {
      this.closeMenu();
    }
  }
};
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  width: 100%;
  background-color: white;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  z-index: 1000;
}

.header-container {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 1rem;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 64px;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: #2563eb;
  text-decoration: none;
}

.nav-desktop {
  display: none;
  gap: 2rem;
}

.nav-desktop a,
.nav-mobile a {
  text-decoration: none;
  color: #475569;
  font-weight: 500;
  transition: color 0.3s;
}

.nav-desktop a:hover,
.nav-desktop a.active,
.nav-mobile a.active {
  color: #2563eb;
}

.menu-button {
  display: block;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #0f172a;
}

.nav-mobile {
  display: block;
  padding-bottom: 1rem;
}

.nav-mobile a {
  display: block;
  padding: 0.5rem 0;
}

@media (min-width: 768px) {
  .nav-desktop {
    display: flex;
  }
  
  .menu-button {
    display: none;
  }
  
  .nav-mobile {
    display: none;
  }
}
</style>