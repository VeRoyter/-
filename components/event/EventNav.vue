<template>
  <nav class="event-nav">
    <NuxtLink to="/" class="nav-btn">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M15.41 7.41L14 6L8 12L14 18L15.41 16.59L10.83 12L15.41 7.41Z" fill="#333333"/>
      </svg>
      <span>Назад</span>
    </NuxtLink>
    <h1 class="page-title">{{ title }}</h1>
    <button class="nav-btn map-btn">
      <span>На карте</span>
      <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M9 1.5C6.1005 1.5 3.75 3.8505 3.75 6.75C3.75 11.25 9 16.5 9 16.5C9 16.5 14.25 11.25 14.25 6.75C14.25 3.8505 11.8995 1.5 9 1.5ZM9 8.625C8.004 8.625 7.125 7.746 7.125 6.75C7.125 5.754 8.004 4.875 9 4.875C9.996 4.875 10.875 5.754 10.875 6.75C10.875 7.746 9.996 8.625 9 8.625Z" fill="#70232F"/>
      </svg>
    </button>
  </nav>
</template>

<script setup>
defineProps({
  title: {
    type: String,
    required: true,
  },
});
</script>

<style scoped>
/* Главный контейнер навигации */
.event-nav {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0px;
  gap: 20px;
  width: 100%;
  height: 40px;
}

/* Заголовок страницы */
.page-title {
  font-family: 'Montserrat', sans-serif;
  font-weight: 600;
  font-size: 24px;
  line-height: 29px;
  color: #2F050F;
  text-align: center;
  /* Позволяет заголовку занимать центральное пространство */
  flex-grow: 1; 
}

/* Общий стиль для кнопок */
.nav-btn {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0px 20px;
  gap: 10px;
  height: 40px;
  background: #FFFFFF;
  border: none;
  border-radius: 5px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 20px;
  color: #333333;
  cursor: pointer;
  text-decoration: none;
  white-space: nowrap;
  flex-shrink: 0; /* Предотвращает сжатие кнопок */
}

.nav-btn:hover {
  background: #f5f5f5;
}
</style>
