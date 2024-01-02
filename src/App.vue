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

<style lang="scss">
#layout {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.events {
  display: flex;
  flex-direction: column;
  align-items: center;
  max-width: 20rem;
  margin-inline: auto;
}

nav {
  padding: 0.25rem 1.0rem;

  &.pagination {
    display: grid;
    grid-template-columns: 6.6rem 6.6rem 6.6rem;


    a {
      font-weight: bold;
      text-decoration: none;
      color: #2c3e50;


      &.router-link-exact-active {
        color: #42b983;
      }

      &:first-child {
        text-align: left;
      }

      &:last-child {
        text-align: right;
      }
    }
  }
}


h2 {
  font-size: 1.25rem;
}
</style>
