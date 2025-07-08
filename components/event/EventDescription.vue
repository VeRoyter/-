<template>
  <div class="cards-wrapper">
    <div class="card">
      <div class="card-content">
        <div class="description-block">
          <div class="header">ОПИСАНИЕ</div>
          <!-- Используем eventData.description, как в рабочем компоненте -->
          <p class="info-text"> 
            {{ eventData.description }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// Определяем props точно так же, как в EventDetailHeader.vue
defineProps({
  eventData: {
    type: Object,
    required: true,
    default: () => ({
      description: 'Описание для этого мероприятия еще не добавлено.'
    })
  }
});
</script>

<style scoped>
.card {
  box-sizing: border-box;
  display: flex;
  background: #FFFFFF;
  border-top: 2px solid #70232F;
  border-radius: 5px;
  padding: 20px;
  width: 100%;
}
.cards-wrapper {
  width: 100%;
}
.header {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 18px;
  color: #70232F;
  margin-bottom: 10px; 
}
.description-block {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  width: 100%;
}
.info-text {
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.6;
  color: #333333;
  margin: 0;
  white-space: pre-wrap; 
}
</style>
