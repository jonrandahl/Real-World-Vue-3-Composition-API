<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div id="layout">
    <header>
      <div class="wrapper">
        <nav>
          <RouterLink :to="{ name: 'EventList' }">Events</RouterLink> |
          <RouterLink :to="{ name: 'About' }">About</RouterLink>
        </nav>
      </div>
    </header>
    <RouterView />
  </div>
</template>

<style>
#layout {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
nav {
  padding: 2rem;
}
nav a {
  font-weight: bold;
  color: #2c3e50;
}
nav a.router-link-exact-active {
  color: #42b983;
}
nav a.disabled {
  color: #ccc;
  cursor: not-allowed;
}
h2 {
  font-size: 1.25rem;
}</style>
