<script setup lang="ts">
import EventCard from '@/components/EventCard.vue'
import router from '@/router'
import EventService from '@/services/EventService.ts'
import { onMounted, ref, computed, watchEffect } from 'vue'
import { Z_UNKNOWN } from 'zlib'

const totalEvents = ref(0) // Store the total events

const props = defineProps(['page'])

const events = ref(null)

const page = computed(() => props.page || 1)

const hasNextPage = computed(() => {
  // Calculate totalPages, based on 2 per page
  const totalPages = Math.ceil(totalEvents.value / 2)

  // If current page is less than total pages, return true
  return page.value < totalPages
})

onMounted(() => {
  watchEffect(() => {
    events.value = null;
    EventService.getEvents(2, page.value)
      .then((response) => {
        events.value = response.data;
        totalEvents.value = response.headers["x-total-count"];
      })
      .catch(() => {
        router.push({ name: 'NetworkError' })
      });
  });
});
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />

    <nav class="pagination">
      <span>
        <router-link :to="{ name: 'EventList', query: { page: page - 1 } }" v-if="page != 1">&#60; Prev</router-link>
      </span>
      <span>
        Page {{ page }}
      </span>
      <span>
        <router-link :to="{ name: 'EventList', query: { page: page + 1 } }" v-if="hasNextPage">Next &#62;</router-link>
      </span>
    </nav>

  </div>
</template>

<style lang="scss" scoped>
</style>
