// pages/events/[id].vue
<template>
  <div class="page-container">
    <Header />
    <div class="content-container">
      <!-- "Хлебные крошки" и кнопка "На карте" -->
      <EventNav :title="event.title" />

      <!-- Если данные загружаются -->
      <div v-if="pending">Загрузка...</div>
      
      <!-- Если произошла ошибка -->
      <div v-else-if="error || !event">Не удалось загрузить событие.</div>

      <!-- Если все хорошо, отображаем компоненты -->
      <div v-else class="event-details-layout">
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
import Header from '@/layouts/Header.vue';
// Импортируем новые компоненты, которые создадим ниже
// import EventNav from '@/components/event/EventNav.vue';
// import EventDetailHeader from '@/components/event/EventDetailHeader.vue';
// import EventGroups from '@/components/event/EventGroups.vue';
// import EventSchedule from '@/components/event/EventSchedule.vue';
// import EventDescription from '@/components/event/EventDescription.vue';
// import ProgramAccordion from '@/components/event/ProgramAccordion.vue';

const route = useRoute();
const eventId = route.params.id;

// Запрашиваем данные для одного события по его ID
const { data: event, pending, error } = await useFetch(`/api/events`, {
    params: { id: eventId },
    // Ключ 'key' важен для кэширования и предотвращения повторных запросов
    key: `event-${eventId}`
});

// Если событие не найдено, можно показать страницу ошибки
if (!event.value || event.value.error) {
  throw createError({ statusCode: 404, statusMessage: 'Событие не найдено', fatal: true });
}
</script>

<style scoped>
  /* Стили для контейнеров, можно взять из index.vue */
  .page-container { background: #EFEFEF; min-height: 100vh; }
  .content-container { max-width: 1480px; margin: 20px auto; }
  .event-details-layout {
    display: flex;
    flex-direction: column;
    gap: 20px;
    background: #fff;
    border-radius: 15px;
    padding: 40px;
  }
</style>
