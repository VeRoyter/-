<template>
  <div class="detail-header-card">
    <div class="content-wrapper">
      <div class="image-container">
        <NuxtImg 
          :src="eventData.cardImage || '/public/images/1_powerlift.jpg'" 
          width="200"
          height="200"
          :alt="eventData.title"
          fit="cover"
        />
      </div>
      
      <div class="main-info-wrapper">
        <div class="info-section">
          <div class="status-tag">Набор открыт</div>
          <div class="info-row">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M12 12C13.6569 12 15 10.6569 15 9C15 7.34315 13.6569 6 12 6C10.3431 6 9 7.34315 9 9C9 10.6569 10.3431 12 12 12ZM12 14C8.13401 14 5 17.134 5 21H19C19 17.134 15.866 14 12 14Z" fill="#70232F"/></svg>
            <span>{{ eventData.age }}</span>
          </div>
          <div class="info-row">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M12 2C8.13 2 5 5.13 5 9C5 14.25 12 22 12 22C12 22 19 14.25 19 9C19 5.13 15.87 2 12 2Z" fill="#70232F"/></svg>
            <span>{{ eventData.location }}</span>
          </div>
          <div class="info-row">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M10 20V14H14V20H19V12H22L12 3L2 12H5V20H10Z" fill="#70232F"/></svg>
            <span>{{ eventData.building }}</span>
          </div>
        </div>
        
        <div class="actions-section">
          <div 
            v-if="eventData.tags && eventData.tags.length > 0" 
            :class="['price-tag', `tag--${eventData.tags[0].type}`]"
          >
            {{ eventData.tags[0].text }}
          </div>
          <button class="apply-btn">Записаться</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  eventData: {
    type: Object,
    required: true,
  },
});
</script>

<style scoped>
.detail-header-card {
  box-sizing: border-box;
  padding: 20px;
  background: #FFFFFF;
  border-top: 2px solid #70232F;
  border-radius: 5px;
  width: 100%;
}

.content-wrapper {
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  gap: 20px;
}

.image-container {
  width: 200px;
  height: 200px;
  border-radius: 10px;
  overflow: hidden;
  flex-shrink: 0;
  background-color: #f0f0f0;
}
.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.main-info-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: stretch;
  height: 200px;
}

.info-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
}

.status-tag {
  box-sizing: border-box;
  padding: 5px 15px;
  border: 1px solid #D86B79;
  border-radius: 5px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  color: #2F050F;
}

.info-row {
  display: flex;
  align-items: center;
  gap: 10px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  color: #333333;
}
.info-row svg {
  flex-shrink: 0;
}

.actions-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.price-tag {
  padding: 5px 15px;
  border-radius: 5px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  white-space: nowrap;
}
.tag--free, .tag--paid {
  background: #D86B79;
  color: #FFFFFF;
}
.tag--trial {
  border: 1px solid #D86B79;
  background: #FFFFFF;
  color: #2F050F;
}

.apply-btn {
  padding: 10px 20px;
  background: #70232F;
  border-radius: 5px;
  border: none;
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;
  color: #FFFFFF;
  cursor: pointer;
}
</style>
