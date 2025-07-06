<template>
  <div class="page-container">
    <Header />
    
    <div class="content-container">
      <Navbar />
      
      <div class="main-content">
        <div class="events-column">
          <div class="events-list">
            Силовой спорт
            <EventCard 
              v-for="event in events" 
              :key="event.id" 
              :event-data="event" 
            />
            Силовой спорт
            <EventCard 
              v-for="event in events" 
              :key="event.id" 
              :event-data="event" 
            />
          </div>
        </div>
        
        <aside class="filters-column">
          Фильтры
          <FiltersPanel />
        </aside>
      </div>
    </div>
  </div>
</template>

<script setup>
import Header from '@/layouts/Header.vue'
import Navbar from '@/layouts/Navbar.vue'
import EventCard from '@/components/common/EventCard.vue'
import FiltersPanel from '@/components/common/FiltersPanel.vue'

// Получаем список всех событий с нашего API
const { data: events, pending, error } = await useFetch('/api/events');
</script>

<style scoped>
.page-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  
}

.content-container {
  background: #EFEFEF;
  border-radius: 15px;
  padding: 40px;
  gap: 20px;
  max-width: 1480px;
  width: calc(100% - 40px);
  margin: 20px auto 40px; 
}

.main-content {
  display: flex;
  gap: 30px;
  margin-top: 20px;
}

.events-column {
  border-radius: 10px;
  padding: 20px;
  flex: 1;
}

.events-list {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.filters-column {
  width: 300px;
  top: 20px;
  align-self: flex-start;
}

@media (max-width: 1200px) {
  .content-container {
    margin-top: 120px;
    padding: 30px;
  }
  
  .main-content {
    flex-direction: column;
  }
  
  .filters-column {
    position: static;
    width: 100%;
    order: -1;
    margin-bottom: 30px;
  }
}

@media (max-width: 768px) {
  .content-container {
    padding: 20px;
    margin-top: 100px;
    width: calc(100% - 20px);
  }
}

@media (max-width: 576px) {
  .content-container {
    padding: 15px;
    margin-top: 90px;
  }
  
  .events-column {
    padding: 15px;
  }
}
</style>