<template>
  <div class="content-container">
    <div v-if="pending">Загрузка...</div>
    <div v-else-if="error || !event">Не удалось загрузить событие.</div>
    <div v-else class="event-details-layout">
      
      <!-- Заголовок страницы, как на главной -->
      <h3 class="page-title">{{ event.title }}</h3>

      <EventDetailHeader :event-data="event" />

       <!-- <div class="groups-section" v-if="event.groups && event.detailedSchedule"> -->
        <EventGroupCard 
          v-for="(group, index) in event.groups"
          :key="index"
          :group="group"
          :schedule="event.detailedSchedule[0]" 
        />
      <!-- </div> -->
    </div>
  </div>
</template>

<script setup>
const route = useRoute();
const eventId = route.params.id;

definePageMeta({
  layout: 'details'
});

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
    /* margin: 20px auto;  */
  }
  .event-details-layout {
    display: flex;
    flex-direction: column;
    gap: 20px;
    background: #EFEFEF;
    border-radius: 15px;
    padding: 40px;
  }
  
  /* Стили для нового заголовка, как в макете */
  .page-title {
    font-family: 'Montserrat', sans-serif;
    font-weight: 600;
    font-size: 24px;
    line-height: 29px;
    color: #2F050F;
    margin: 0; /* Убираем лишний отступ, так как gap уже есть */
  }
</style>
