<script setup lang="ts">
  defineProps({
    resource: {
      type: String,
      required: true,
      default: 'page',
    },
  })
</script>

<template>
  <div>
    <h1>Oops!</h1>
    <h2>Sorry, the {{ resource }} you are looking for does not exist.</h2>
    <router-link :to="{ name: 'EventList' }">Back to the home page</router-link>
  </div>
</template>
