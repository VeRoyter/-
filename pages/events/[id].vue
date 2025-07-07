// pages/events/[id].vue
<template>
  <div>
    <Header />
    <div class="content-container">
      <div v-if="pending">Загрузка...</div>
      <div v-else-if="error || !event">Не удалось загрузить событие.</div>
      <div v-else class="event-details-layout">
        <EventNav :title="event.title" />
        <EventDetailHeader :event-data="event" />
        <EventGroups :groups="event.groups" />
        <EventSchedule :schedule="event.detailedSchedule" />
        <EventDescription :text="event.description" />
        <ProgramAccordion :items="event.program" />
      </div>
    </div>
  </div>
</template>

<script setup>

const route = useRoute();
const eventId = route.params.id;

const { data: event, pending, error } = await useFetch(`/api/events`, {
    params: { id: eventId },
    key: `event-${eventId}`
});

if (!event.value || event.value.error) {
  throw createError({ statusCode: 404, statusMessage: 'Событие не найдено', fatal: true });
}
</script>

<style scoped>
  .content-container { 
    max-width: 1480px; 
    margin: 20px auto; 
  }
  .event-details-layout {
    display: flex;
    flex-direction: column;
    gap: 20px;
    background: #EFEFEF;
    border-radius: 15px;
    padding: 40px;
  }
</style>
