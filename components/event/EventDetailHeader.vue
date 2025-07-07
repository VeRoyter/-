<template>
  <div class="event-card">
    <div class="image-container">
      <NuxtImg
        :src="eventData.mainImage || '/images/default-placeholder.svg'"
        :alt="eventData.title"
        class="event-image"
      />
    </div>

    <div class="info-wrapper">
      <div class="top-content">
        <div class="tags-header">
          <div class="status-tag">Набор открыт</div>
          <div
            v-if="eventData.tags && eventData.tags.length > 0"
            :class="['price-tag', `tag--${eventData.tags[0].type}`]"
          >
            {{ eventData.tags[0].text }}
          </div>
        </div>

        <div class="details-section">
          <div class="info-row">
            <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M9 9C10.3807 9 11.5 7.88071 11.5 6.5C11.5 5.11929 10.3807 4 9 4C7.61929 4 6.5 5.11929 6.5 6.5C6.5 7.88071 7.61929 9 9 9ZM9 10.5C5.82843 10.5 3.25 13.0784 3.25 16.25H14.75C14.75 13.0784 12.1716 10.5 9 10.5Z" fill="#70232F"/></svg>
            <span>{{ eventData.age }}</span>
          </div>
          <div class="info-row">
            <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M9 1.5C6.10051 1.5 3.75 3.85051 3.75 6.75C3.75 10.6875 9 16.5 9 16.5C9 16.5 14.25 10.6875 14.25 6.75C14.25 3.85051 11.8995 1.5 9 1.5Z" fill="#70232F"/></svg>
            <span>{{ eventData.location }}</span>
          </div>
          <div class="info-row">
            <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M7.5 15V10.5H10.5V15H14.25V9H16.5L9 2.25L1.5 9H3.75V15H7.5Z" fill="#70232F"/></svg>
            <span>{{ eventData.building }}</span>
          </div>
        </div>
      </div>

      <div class="action-footer">
        <button class="apply-btn">Записаться</button>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  eventData: {
    type: Object,
    required: true,
    default: () => ({
      mainImage: '',
      title: 'Название мероприятия',
      age: '10-18 лет',
      location: 'г. Иркутск, Юбилейный мкр., стр. 49/1',
      building: 'ФОК "Юбилейный"',
      tags: [{ text: 'Бесплатно', type: 'free' }]
    })
  },
});
</script>

<style scoped>
/* Основной контейнер карты */
.event-card {
  box-sizing: border-box;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  padding: 20px;
  gap: 20px;
  background: #FFFFFF;
  border-top: 2px solid #70232F;
  border-radius: 5px;
  width: 100%;
  font-family: 'Montserrat', sans-serif;
}

/* Контейнер изображения */
.image-container {
  width: 200px;
  height: 200px;
  flex-shrink: 0;
  border-radius: 10px;
  overflow: hidden;
}
.event-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.info-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: stretch; /* ИСПРАВЛЕНО: Растягиваем дочерние элементы */
  height: 200px;
}

/* Верхняя часть с тегами и деталями */
.top-content {
  width: 100%; /* Растягиваем, чтобы занять всю доступную ширину */
  align-self: stretch; 
  display: flex;
  flex-direction: column;
  gap: 20px;
}

/* Блок с тегами "Набор открыт" и "Бесплатно" */
.tags-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

/* Блок с деталями (возраст, адрес) */
.details-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
}

/* Строка с иконкой и текстом */
.info-row {
  display: flex;
  align-items: center;
  gap: 10px;
  font-weight: 400;
  font-size: 14px;
  line-height: 17px;
  color: #333333;
}
.info-row svg {
  flex-shrink: 0;
}

/* Тег "Набор открыт" */
.status-tag {
  box-sizing: border-box;
  padding: 5px 15px;
  border: 1px solid #D86B79;
  border-radius: 5px;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  color: #2F050F;
}

/* Тег цены */
.price-tag {
  padding: 5px 15px;
  border-radius: 5px;
  font-weight: 600;
  font-size: 12px;
  line-height: 15px;
  color: #FFFFFF;
  background: #D86B79;
}

/* Нижняя часть с кнопкой */
.action-footer {
  display: flex;
  justify-content: flex-end;
}

/* Кнопка "Записаться" */
.apply-btn {
  padding: 10px 20px;
  background: #70232F;
  border-radius: 5px;
  border: none;
  font-weight: 600;
  font-size: 16px;
  line-height: 20px;
  color: #FFFFFF;
  cursor: pointer;
}
</style>
