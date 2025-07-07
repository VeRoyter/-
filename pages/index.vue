<template>
  <div class="page-container">
    <Header />
    
    <div class="content-container">
      <Navbar />
      
      <div class="main-content">
        <div class="events-column">
          <div v-for="categoryGroup in categorizedEvents" :key="categoryGroup.name" class="events-group">
            <h3 class="category-title">{{ categoryGroup.name }}</h3>

            <div class="events-list">
              <EventCard 
                v-for="event in categoryGroup.events" 
                :key="event.id" 
                :event-data="event" 
              />
            </div>
          </div>
        </div>
        
        <aside class="filters-column">
          <h3 class="filters-title">Фильтры</h3>
          <FiltersPanel />
        </aside>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue';
import Header from '@/components/common/Header.vue';
import Navbar from '@/components/common/Navbar.vue';
import EventCard from '@/components/common/EventCard.vue';
import FiltersPanel from '@/components/common/FiltersPanel.vue';

const { data: allEvents, pending } = await useFetch('/api/events');

const categorizedEvents = computed(() => {
  if (!allEvents.value) return [];

  const groups = allEvents.value.reduce((acc, event) => {
    const category = event.category;
    
    if (!acc[category]) {
      acc[category] = {
        name: category,
        events: []
      };
    }
    
    acc[category].events.push(event);
    
    return acc;
  }, {});
  
  return Object.values(groups);
});
</script>

<style scoped>
.page-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  max-width: 1480px;
  margin: auto;
}

.content-container {
  background: #EFEFEF;
  border-radius: 15px;
  padding: 40px;
  max-width: 1480px;
  margin: 20px auto 40px; 
}

.main-content {
  display: flex;
  gap: 30px;
  margin-top: 20px;
}

.events-column {
  flex: 1;
}

.events-group {
  margin-bottom: 40px; /* Отступ между категориями */
}
.events-group:last-child {
  margin-bottom: 0;
}

.events-list {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.category-title, .filters-title {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 24px;
  line-height: 1;
  color: #333333;
  margin: 0 0 20px 0;
}

.filters-title {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 24px;
  line-height: 1;
  color: #333333;
  margin: 0 0 0 0;
}

.filters-column {
  width: 330px;
  flex-shrink: 0;
  top: 20px;
  align-self: flex-start;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

@media (max-width: 1200px) {
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
</style>
