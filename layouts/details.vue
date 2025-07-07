<template>
  <div class="page-container">
    <CommonHeader logo="logo_2.svg" />
    <div class="content-container">
      <!-- <CommonNavbar /> -->
      <EventNav />
      <main>
        <slot />
      </main>
    </div>
  </div>
</template>

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
  
  /* --- Добавленные строки --- */
  width: 100%;             /* Занимать всю доступную ширину */
  box-sizing: border-box;   /* Включить padding в расчет ширины */
}
</style>
