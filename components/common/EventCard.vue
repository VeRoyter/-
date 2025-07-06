<template>
  <div class="event-card">
    <div class="card-image">
      <NuxtImg 
        :src="eventData.cardImage || '/public/images/1_powerlift.jpg'" 
        width="200"
        height="200"
        :alt="eventData.title"
        fit="cover"
      />

    </div>
    
    <div class="card-main-content">
      <div class="card-header">
        <h3 class="event-title">{{ eventData.title }}</h3>
        <div class="tags-container">
          <div 
            v-for="(tag, index) in eventData.tags" 
            :key="index" 
            :class="['tag', `tag--${tag.type}`]"
          >
            <span>{{ tag.text }}</span>
          </div>
        </div>
      </div>

      <div class="card-bottom-row">
        <div class="event-info">
          <div class="hashtag">{{ eventData.hashtag }}</div>
          
          <div class="info-row">
            <div class="icon">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M12 12C13.6569 12 15 10.6569 15 9C15 7.34315 13.6569 6 12 6C10.3431 6 9 7.34315 9 9C9 10.6569 10.3431 12 12 12ZM12 14C8.13401 14 5 17.134 5 21H19C19 17.134 15.866 14 12 14Z" fill="#70232F"/></svg>
            </div>
            <span>{{ eventData.age }}</span>
          </div>
          
          <div class="info-row">
            <div class="icon">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M12 11.5C12.8284 11.5 13.5 10.8284 13.5 10C13.5 9.17157 12.8284 8.5 12 8.5C11.1716 8.5 10.5 9.17157 10.5 10C10.5 10.8284 11.1716 11.5 12 11.5Z" fill="#70232F"/><path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2ZM12 12.5C10.62 12.5 9.5 11.38 9.5 10C9.5 8.62 10.62 7.5 12 7.5C13.38 7.5 14.5 8.62 14.5 10C14.5 11.38 13.38 12.5 12 12.5Z" fill="#70232F"/></svg>
            </div>
            <span>{{ eventData.location }}</span>
          </div>
          
          <div class="info-row">
            <div class="icon">
              <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M10 20V14H14V20H19V12H22L12 3L2 12H5V20H10Z" fill="#70232F"/></svg>
            </div>
            <span>{{ eventData.building }}</span>
          </div>
          
          <div class="schedule">
            <div class="schedule-header">
              <div class="icon">
                <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M11.99 2C6.47 2 2 6.48 2 12C2 17.52 6.47 22 11.99 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 11.99 2ZM12 20C7.58 20 4 16.42 4 12C4 7.58 7.58 4 12 4C16.42 4 20 7.58 20 12C20 16.42 16.42 20 12 20Z" fill="#70232F"/><path d="M12.5 7H11V13L16.25 16.15L17 14.92L12.5 12.25V7Z" fill="#70232F"/></svg>
              </div>
              <div class="days">{{ eventData.schedule.days }}</div>
            </div>
            <div class="time-slots">
              <div class="time-slot" v-for="(slot, index) in eventData.schedule.slots" :key="index">{{ slot }}</div>
            </div>
          </div>
        </div>
        
        <div class="card-action">
          <NuxtLink :to="`/events/${eventData.id}`" class="details-btn">
            Подробнее
          </NuxtLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  eventData: {
    type: Object,
    required: true
  }
});
</script>

<style scoped>
.event-card {
  box-sizing: border-box;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 20px;
  gap: 10px;
  width: 100%;
  background: #FFFFFF;
  border-top: 2px solid #70232F;
  border-radius: 5px;
}

.card-image {
  width: 200px;
  height: 200px;
  flex-shrink: 0;
  background: #F0F0F0;
  border-radius: 5px;
  overflow: hidden;
}

.card-main-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 10px;
}

.event-title {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
  margin: 0;
}

.tags-container {
  display: flex;
  gap: 20px;
}
.tag {
  display: flex;
  align-items: center;
  padding: 5px 15px;
  gap: 10px;
  background: #D86B79;
  border-radius: 5px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  font-size: 12px;
  line-height: 15px;
  color: #FFFFFF;
  white-space: nowrap;
}
.tag--trial {
  background: #FFFFFF;
  color: #2F050F;
  border: 1px solid #D86B79;
}

.card-bottom-row {
  display: flex;
  align-items: flex-end;
  gap: 10px;
  margin-top: auto;
}

.event-info {
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.hashtag {
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  color: #D86B79;
}

.info-row {
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
}
.icon {
  width: 18px;
  height: 18px;
  flex-shrink: 0;
}

.schedule {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}
.schedule-header {
  display: flex;
  align-items: center;
  gap: 10px;
}
.days {
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
}
.time-slots {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.time-slot {
  padding: 4px 10px;
  background: #F7DAAB;
  border-radius: 5px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 20px;
  color: #333333;
}


.details-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 20px;
  gap: 10px;
  background: #70232F;
  border-radius: 5px;
  text-decoration: none;
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  font-size: 14px;
  line-height: 17px;
  color: #FFFFFF;
  cursor: pointer;
}

/* Адаптивность */
@media (max-width: 768px) {
  .event-card {
    flex-direction: column;
  }
  .card-image {
    width: 100%;
    height: 180px;
  }
  .card-main-content {
    width: 100%;
  }
  .card-bottom-row {
    flex-direction: column;
    align-items: flex-start;
  }
  .card-action {
    align-self: flex-end;
    margin-top: 15px;
  }
}
</style>
