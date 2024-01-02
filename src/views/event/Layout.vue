<script setup lang="ts">
import { ref, onMounted } from 'vue'
import EventService from '@/services/EventService'

const props = defineProps({
  id: {
    type: String,
    required: true,
  },
})
const event = ref(null)

onMounted(async () => {
  await EventService.getEvent(props.id)
    .then((response) => {
      event.value = response.data
    })
    .catch((error) => {
      console.log(error)
    })
})
</script>

<template>
  <div class="events">
    <div v-if="event">
      <h1>{{ event.title }}</h1>
      <nav class="pagination">
        <router-link :to="{ name: 'EventDetails' }">Details</router-link>
        <router-link :to="{ name: 'EventRegister' }">Register</router-link>
        <router-link :to="{ name: 'EventEdit' }">Edit</router-link>
      </nav>
      <router-view :event="event" />
    </div>
  </div>
</template>
