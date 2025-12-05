<template>
  <div id="app">
    <Header />
    <main class="main-content">
      <router-view />
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    Footer
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  line-height: 1.6;
  color: #0f172a;
  background-color: #f8fafc;
}

.main-content {
  min-height: calc(100vh - 200px);
  padding-top: 64px;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Responsive images */
img {
  max-width: 100%;
  height: auto;
}

/* Focus styles */
:focus {
  outline: 2px solid #2563eb;
  outline-offset: 2px;
}

/* Remove focus for mouse users */
:focus:not(:focus-visible) {
  outline: none;
}
</style>