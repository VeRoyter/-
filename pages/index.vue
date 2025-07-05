<template>
  <header class="header">
    <div class="logo-container">
      <div class="logo">
        <NuxtImg 
          src="/images/logo.svg" 
          width="76"
          height="76"
          alt="KidsConnect Logo"
          loading="eager"
        />
      </div>
      <div class="site-name">KidsConnect</div>
    </div>
  </header>
</template>

<script setup>
// Логика компонента (при необходимости)
</script>

<style scoped>
.header {
  /* Основные стили контейнера */
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 12px 40px;
  gap: 10px;
  
  /* Позиционирование и размеры */
  position: absolute;
  width: 1480px;
  height: 100px;
  left: 220px;
  top: 20px;
  
  /* Внешний вид */
  background: #70232F;
  border-radius: 15px;
  box-sizing: border-box;
  z-index: 1000;
  
  /* Центрирование для адаптива */
  transform: translateX(-50%);
  left: 50%;
  max-width: calc(100% - 40px);
}

.logo-container {
  /* Внутренний flex-контейнер */
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 0px;
  gap: 18px;
  
  /* Размеры */
  width: 304px;
  height: 76px;
  
  /* Для внутреннего расположения */
  flex: none;
  order: 0;
  flex-grow: 0;
}

.logo {
  /* Стили логотипа */
  width: 76px;
  height: 76px;
  flex-shrink: 0;
  border-radius: 16px;
  overflow: hidden;
  
  /* Центрирование изображения */
  display: flex;
  align-items: center;
  justify-content: center;
}

.site-name {
  /* Стили текста */
  width: 210px;
  height: 39px;
  
  font-family: 'Montserrat Alternates', sans-serif;
  font-style: normal;
  font-weight: 600;
  font-size: 32px;
  line-height: 39px;
  color: #FFFFFF;
  
  /* Для внутреннего расположения */
  flex: none;
  order: 1;
  flex-grow: 0;
}

/* Адаптив для меньших экранов */
@media (max-width: 1600px) {
  .header {
    width: 1200px;
    left: calc(50% - 600px);
  }
}

@media (max-width: 1300px) {
  .header {
    width: 1000px;
    left: calc(50% - 500px);
  }
}

@media (max-width: 1100px) {
  .header {
    width: 90%;
    left: 5%;
    transform: none;
    padding: 12px 20px;
  }
  
  .logo-container {
    width: auto;
    gap: 12px;
  }
  
  .site-name {
    font-size: 28px;
    line-height: 34px;
  }
}

@media (max-width: 768px) {
  .header {
    height: 80px;
    top: 10px;
  }
  
  .logo {
    width: 60px;
    height: 60px;
  }
  
  .site-name {
    font-size: 24px;
    line-height: 29px;
    height: auto;
  }
}

@media (max-width: 480px) {
  .header {
    padding: 8px 15px;
    gap: 5px;
  }
  
  .logo-container {
    gap: 8px;
  }
  
  .site-name {
    font-size: 20px;
    line-height: 24px;
  }
}
</style>